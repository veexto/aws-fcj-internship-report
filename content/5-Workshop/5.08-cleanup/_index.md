---
title: "Resource Cleanup"
date: 2026-11-27
weight: 8
chapter: false
pre: "<b>5.8. </b>"
---

To avoid incurring ongoing charges after completing the workshop, delete the resources in the following order:

1. **Amazon CloudFront:** Select the Distribution → click **Disable** → wait for it to finish, then click **Delete**.
2. **Amazon S3:** Open the `recipe-suggestion-website` bucket → click **Empty** to delete all objects → click **Delete**.
3. **Amazon API Gateway:** Delete the HTTP API `BepThongMinhAPI`.
4. **AWS Lambda:** Delete the `RecipeSearchFunction
