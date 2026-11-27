---
title: "Dọn dẹp tài nguyên"
date: 2026-11-27
weight: 8
chapter: false
pre: "<b>5.8. </b>"
---

Để tránh phát sinh chi phí sau khi hoàn tất bài thực hành, hãy xóa các tài nguyên theo đúng thứ tự sau:

1. **Amazon CloudFront:** Chọn Distribution → bấm **Disable** → chờ hoàn tất rồi bấm **Delete**.
2. **Amazon S3:** Vào bucket `recipe-suggestion-website` → bấm **Empty** để xóa toàn bộ file → bấm **Delete**.
3. **Amazon API Gateway:** Xóa HTTP API `BepThongMinhAPI`.
4. **AWS Lambda:** Xóa hàm `RecipeSearchFunction`.
5. **Amazon DynamoDB:** Xóa bảng `RecipesTable`.
6. **AWS IAM:** Xóa role `RecipesLambdaRole`.
