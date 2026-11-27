---
title: "Deploy AWS Lambda Backend"
date: 2026-11-27
weight: 4
chapter: false
pre: "<b>5.4. </b>"
---

## 1. Create the Lambda Function

1. Navigate to **AWS Lambda → Create function → Author from scratch**.
2. Configure the basic parameters:
  - **Function name:** `RecipeSearchFunction`
  - **Runtime:** `Python 3.12`
  - **Execution role:** Select **Use an existing role** → `RecipesLambdaRole`.
3. Go to **Configuration → General configuration → Edit**, and increase **Timeout** to `15 seconds`.
4. Go to **Configuration → Environment variables**, and add 2 environment variables:
  - `DYNAMODB_TABLE`: `RecipesTable`
  - `BEDROCK_MODEL_ID`: `apac.amazon.nova-micro-v1:0`

---

## 2. Architecture & Functional Breakdown of `lambda_function.py`

The `lambda_function.py` source code is divided into **6 main functional blocks**, handling the entire pipeline from receiving HTTP requests, validating inputs, and connecting to 3 core AWS services (**DynamoDB**, **Amazon Location Service**, **Amazon Bedrock**) to returning standardized JSON responses to the frontend.

### 2.1. Configuration Initialization & AWS SDK Clients
```python
import base64
import json
import logging
import math
import os
import random
import unicodedata
import urllib.error
import urllib.request
from decimal import Decimal
from urllib.parse import parse_qs, quote

import boto3
from botocore.exceptions import ClientError

logger = logging.getLogger()
logger.setLevel(logging.INFO)

REGION = os.environ.get("AWS_REGION", "ap-southeast-1")
BEDROCK_REGION = os.environ.get("BEDROCK_REGION", REGION).strip()
TABLE_NAME = os.environ.get("DYNAMODB_TABLE", "RecipesTable").strip()
BEDROCK_MODEL_ID = os.environ.get("BEDROCK_MODEL_ID", "apac.amazon.nova-micro-v1:0").strip()
BEDROCK_API_KEY = os.environ.get("BEDROCK_API_KEY", "").strip()

MAX_INPUT_LENGTH = 200
MAX_KEYWORDS = 10

dynamodb = boto3.resource("dynamodb", region_name=REGION)
table = dynamodb.Table(TABLE_NAME)
geo_places_client = boto3.client("geo-places", region_name=REGION)
bedrock_client = boto3.client("bedrock-runtime", region_name=BEDROCK_REGION)

CORS_HEADERS = {
    "Access-Control-Allow-Origin": "*",
    "Access-Control-Allow-Headers": "Content-Type,Authorization",
    "Access-Control-Allow-Methods": "GET,POST,OPTIONS",
    "Content-Type": "application/json; charset=utf-8",
}
