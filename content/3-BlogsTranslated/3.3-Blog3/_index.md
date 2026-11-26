---
title: "Blog 3: Re-Running Last Week's Pipeline Gave Totally Different Numbers: Was It a Code Change or an Overwritten S3 File?"
date: 2026-11-26
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Overview: Achieving Data Reproducibility with Amazon S3 Versioning and SHA-256

When building data engineering pipelines or ML training workflows on AWS, most of us initially set up a deceptively clean storage pattern:

- A daily **ETL Ingestion** job overwrites the latest dataset at a single static S3 path, such as `s3://data-lake-bucket/clean/dataset.csv`
- Downstream Lambda functions or EC2 workers read that fixed key to generate reports or train models

Everything runs smoothly until you need to audit historical numbers: you check out last week's exact Git commit and re-run the pipeline against `s3://data-lake-bucket/clean/dataset.csv`, only to get completely different outputs from the submitted report. At that point, you have no way to tell whether a recent code refactor introduced a bug or whether yesterday's ETL job silently overwrote `dataset.csv`. Without pinning input data versions, debugging and compliance audits turn into pure guesswork.

**Original Post:** [View on Facebook](https://www.facebook.com/share/p/151HogtQqMT/)

---

## 1. Why You Should Not Rely on S3 `ETag` for File Integrity

When looking for a quick way to verify whether an S3 object has changed, many developers (myself included) reach for the `ETag` field returned by S3 APIs. However, `ETag` is a classic trap:

- **Only valid for Single-Part Uploads with SSE-S3:** S3 only sets `ETag` to the raw **MD5** digest of the file when uploaded in a single operation (*single-part upload*) using default `SSE-S3` encryption
- **Breaks under Multipart Upload & SSE-KMS:** Once a file exceeds the SDK's multipart threshold (**Multipart Upload**) or the bucket uses **SSE-KMS** encryption, `ETag` is no longer the MD5 of the entire object (for multipart uploads, it becomes the MD5 of the concatenated part MD5s followed by the part count, e.g., `"...-5"`)

Comparing a locally computed file hash against S3's `ETag` will falsely flag intact files as corrupted. Instead of relying on `ETag`, the reliable approach is pairing **SHA-256** checksums (via S3's native `ChecksumAlgorithm='SHA256'` or application-side hashing) with **S3 Versioning**.

---

## 2. Combining S3 Versioning with a DynamoDB SHA-256 Manifest

To reproduce the exact input dataset for any historical pipeline run with 100% certainty, combine three building blocks:

### 2.1. Enable S3 Versioning on the Data Bucket
Every time the ETL job overwrites `clean/dataset.csv`, S3 preserves the previous object and assigns the new upload a unique `VersionId` (e.g., `v1`, `v2`). Older revisions become *Noncurrent Versions* and remain completely immutable—nobody can alter the bytes stored under an existing `VersionId`.

### 2.2. Record a Run Manifest in Amazon DynamoDB
Whenever a pipeline starts a new execution (`Run ID`), it persists a Manifest record capturing the `Bucket`, `Key`, exact `VersionId` consumed, and the object's `SHA-256` digest.

### 2.3. Read by Pinned `VersionId` and Verify SHA-256 Before Processing
When re-running an earlier job for auditing or backtesting, the pipeline ignores the unversioned key (which always resolves to the latest `v2`) and instead queries the DynamoDB Manifest, calls `GetObject` with `VersionId=v1`, computes the `SHA-256` hash of the downloaded byte stream, and compares it against the stored manifest. Only upon an exact match does processing proceed; any mismatch or missing version triggers an immediate **Fail Fast** abort rather than producing silent data corruption.

---

## 3. Pipeline Data Reproducibility Architecture

![Pipeline Data Reproducibility Architecture with S3 Versioning and DynamoDB Manifest](/images/blog3-architecture.png)

- **ETL Ingestion:** Continuously overwrites the dataset key on Amazon S3. With Versioning enabled, `v1` remains preserved alongside `v2`
- **Step 1 (Manifest DB):** The Pipeline Runner writes or reads the pinned object metadata (`VersionId` + `SHA-256` hash) in Amazon DynamoDB
- **Step 2 (`GetObjectVersion`):** The Pipeline Runner retrieves the exact pinned object version (`v1`) rather than accidentally pulling the latest `v2`
- **Step 3 (Integrity Check):** Compares the live `SHA-256` hash against the manifest—proceeding only on a match and failing fast on any discrepancy
- **Automated Cleanup:** An S3 Lifecycle Rule periodically expires aged noncurrent versions (`NoncurrentVersionExpiration`) to keep storage costs bounded

---

## 4. Four Implementation Pitfalls to Watch Out For

### 4.1. Granting `s3:GetObject` While Forgetting `s3:GetObjectVersion`
In IAM policies, `s3:GetObject` only authorizes reading the current version of an object. The moment your pipeline passes a `VersionId` parameter to reproduce historical data, AWS denies the request with `AccessDenied` unless the IAM Role also includes `s3:GetObjectVersion`.

### 4.2. Silent S3 Bill Growth from Unmanaged Noncurrent Versions
In Singapore (`ap-southeast-1`), every noncurrent version on S3 Standard is billed at full storage rates (`$0.025/GB/month` for the first 50 TB). Overwriting a `10 GB` dataset daily for 30 days means paying for `300 GB` (`$7.50/month` instead of `$0.25/month`), even though the default S3 Console view (with *Show versions* toggled off) displays only a single file. Always configure an **S3 Lifecycle Rule** to transition older versions to cheaper storage tiers (`NoncurrentVersionTransition`) or expire them after a retention window (`NoncurrentVersionExpiration`).

### 4.3. Standard `DeleteObject` Calls Do Not Free Storage
On a versioned bucket, calling `DeleteObject` without specifying a `VersionId` does not delete any underlying bytes—it merely inserts a **Delete Marker** as the latest version. All prior versions remain stored and billed monthly until explicitly deleted by their `VersionId`.

### 4.4. Trusting `ETag` Across Multipart Uploads or SSE-KMS
As highlighted in Section 1, always store and validate **SHA-256** checksums (using S3's built-in `ChecksumSHA256` support or streaming hash calculation) rather than treating `ETag` as a cryptographic integrity signature.

---

## 5. How to Verify in 30 Seconds

- **Verify on the S3 Console:** Open your bucket → toggle **"Show versions"** at the top of the object list → confirm each overwrite creates a distinct Version ID row without erasing prior revisions
- **Test the Fail Fast Safeguard:** Manually alter a single character in the `SHA-256` string stored in your DynamoDB Manifest and re-trigger the pipeline → verify that the job immediately halts and raises an integrity validation error

---

## Conclusion

Ensuring reproducible inputs for ETL and AI/ML pipelines on AWS comes down to three core practices:

- **Never rely solely on unversioned S3 paths** when you need to reproduce historical pipeline runs
- **Pin inputs with S3 Versioning + SHA-256 Manifests** (instead of `ETag`) to guarantee byte-for-byte reproducibility
- **Pair IAM permissions with Lifecycle rules:** Include `s3:GetObjectVersion` in your execution role and configure **S3 Lifecycle Rules** to prevent noncurrent versions from inflating storage bills

---

**References:**  
- Using Versioning in S3 Buckets: https://docs.aws.amazon.com/AmazonS3/latest/userguide/Versioning.html  
- Checking Object Integrity in Amazon S3 (SHA-256): https://docs.aws.amazon.com/AmazonS3/latest/userguide/checking-object-integrity.html  
- Managing Noncurrent Versions with S3 Lifecycle: https://docs.aws.amazon.com/AmazonS3/latest/userguide/lifecycle-configuration-examples.html  
- Amazon S3 Pricing (ap-southeast-1): https://aws.amazon.com/s3/pricing/

---

## Author

<div style="display: flex; align-items: flex-start; margin-bottom: 30px; padding: 20px; border: 1px solid #ddd; border-radius: 5px;">
  <img src="/images/avatar.png" alt="Author" style="width: 150px; height: 150px; object-fit: cover; margin-right: 20px; border-radius: 5px;">
  <div>
    <h3 style="margin-top: 0;">AWS First Cloud Journey Intern</h3>
    <p>Cloud engineering intern in the AWS First Cloud Journey (FCJ) program, passionate about distributed systems architecture, performance optimization, and sharing hands-on cloud implementation insights.</p>
  </div>
</div>
