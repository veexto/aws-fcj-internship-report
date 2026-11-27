---
title: "Triển khai Frontend lên S3 & CloudFront"
date: 2026-11-27
weight: 6
chapter: false
pre: "<b>5.6. </b>"
---

> **Lưu ý kỹ thuật:** Trình duyệt web hiện đại chặn API định vị GPS (`navigator.geolocation`) nếu trang web chạy trên giao thức `http://`. Do đó, việc triển khai **Amazon CloudFront** để cung cấp chứng chỉ **HTTPS** là bắt buộc.

#### 1. Cấu hình Amazon S3
1. Tạo S3 bucket tên `recipe-suggestion-website`, bỏ tích **Block all public access**.
2. Thêm **Bucket policy** cho phép đọc công khai:

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
