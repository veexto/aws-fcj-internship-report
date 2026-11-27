---
title: "Cấu hình AWS IAM Role"
date: 2026-11-27
weight: 3
chapter: false
pre: "<b>5.3. </b>"
---

Hàm Lambda cần được cấp quyền đọc dữ liệu từ DynamoDB, gọi mô hình hội thoại trên Amazon Bedrock và truy vấn bản đồ từ Amazon Location Service (`geo-places` v2).

#### Các bước thực hiện

1. Truy cập **IAM → Roles → Create role**.
2. Chọn **AWS service** → **Lambda** → bấm **Next**.
3. Tìm và gắn policy `AWSLambdaBasicExecutionRole` để ghi log ra Amazon CloudWatch.
4. Đặt tên Role là `RecipesLambdaRole` và bấm **Create role**.
5. Mở lại `RecipesLambdaRole`, chọn **Add permissions → Create inline policy (JSON)** và dán nội dung sau:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "dynamodb:Scan",
        "dynamodb:GetItem",
        "dynamodb:Query"
      ],
      "Resource": "arn:aws:dynamodb:ap-southeast-1:*:table/RecipesTable"
    },
    {
      "Effect": "Allow",
      "Action": [
        "bedrock:InvokeModel"
      ],
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": [
        "geo-places:Geocode",
        "geo-places:SearchText",
        "geo-places:SearchNearby",
        "geo-places:ReverseGeocode"
      ],
      "Resource": "*"
    }
  ]
}
