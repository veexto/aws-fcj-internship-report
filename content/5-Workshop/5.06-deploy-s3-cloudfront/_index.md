---
title: "Deploy Frontend to S3 & CloudFront"
date: 2026-11-27
weight: 6
chapter: false
pre: "<b>5.6. </b>"
---

> **Technical Note:** Modern web browsers block the GPS Geolocation API (`navigator.geolocation`) when a website is served over `http://`. Therefore, deploying **Amazon CloudFront** to provide an **HTTPS** certificate is mandatory.

#### 1. Configure Amazon S3
1. Create an S3 bucket named `recipe-suggestion-website` and uncheck **Block all public access**.
2. Add a **Bucket policy** to allow public read access:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::recipe-suggestion-website/*"
    }
  ]
}
