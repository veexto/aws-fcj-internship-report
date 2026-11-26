---
title: "AWS Technical Blogs"
date: 2026-09-14
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

This section compiles **3 in-depth technical blog posts** distilled from hands-on lab experiments, load testing, and real-world operational troubleshooting on **Amazon Web Services (AWS)**:

### [Blog 1 - Web Auto Scaling Works Great, So Why Do 10,000 Users Still See Endless Loading Spinners?](3.1-Blog1/)
This article dissects database-tier bottlenecks that emerge when a horizontally scaled web tier (**Auto Scaling Group**) faces 10,000 concurrent users. It walks through a two-tier read optimization strategy combining **Amazon ElastiCache (Redis)** with a **Cache-Aside (Lazy Loading)** pattern and **Amazon RDS Read Replicas** to offload heavy read queries, while highlighting four common operational pitfalls: confusing Multi-AZ Standby instances with Read Replicas, asynchronous replication lag, Cache Stampede expiration spikes, and cost management in the Singapore (`ap-southeast-1`) region.

### [Blog 2 - S3 and EC2 Are in the Same Region—Why Does My NAT Gateway Bill Keep Climbing Every Month?](3.2-Blog2/)
This article uncovers the hidden intra-region data processing charges incurred when compute workloads inside a **Private Subnet** communicate with **Amazon S3** and **Amazon DynamoDB** through a default `0.0.0.0/0` route traversing a **NAT Gateway**. It explains how **VPC Gateway Endpoints** leverage **Longest Prefix Match** routing to keep traffic within the AWS Private Backbone at **$0/GB**, alongside four critical configuration traps: distinguishing Gateway from Interface Endpoints, associating Private Route Tables, same-region constraints, and adding `aws:PrincipalArn` exclusions when locking down S3 Bucket Policies with `aws:SourceVpce`.

### [Blog 3 - Re-Running Last Week’s Pipeline Produced Completely Different Numbers: Was It a Code Change or an Overwritten S3 File?](3.3-Blog3/)
This article tackles **data reproducibility** for ETL pipelines and AI/ML training workflows on AWS when upstream S3 objects are continuously overwritten. Rather than relying on S3 `ETag` values—which break down under Multipart Uploads or SSE-KMS encryption—it outlines an architecture pairing **Amazon S3 Versioning** (pinning immutable `VersionId` references) with an **Amazon DynamoDB Manifest** storing **SHA-256** checksums for **Fail-Fast** integrity validation, plus practical notes on `s3:GetObjectVersion` IAM permissions and **S3 Lifecycle Rules** for cleaning up noncurrent versions.
