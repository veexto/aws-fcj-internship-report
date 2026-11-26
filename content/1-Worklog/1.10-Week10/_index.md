---
title: "Week 10 Worklog"
date: 2026-11-16
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Week 10 Objectives:
- Harden backend security practices and standardize cloud identity and access workflows.
- Complete **Amazon Cognito** integration with token-based authentication and session refresh flows.
- Enforce strict data validation, access pattern modeling, and secondary indexing on **Amazon DynamoDB**.
- Implement custom **API Gateway** authorizers alongside request throttling and rate limiting.
- Connect core serverless components into a cohesive end-to-end backend pipeline.

---

### Weekly Action Plan:

| Day | Task | Start Date | Completion Date | Reference Material |
|-----|------|-------------|------------------|--------------------|
| 2 | - Analyze token-based authentication and authorization flows (JWT structure, Access Token, ID Token) <br>- Review **OWASP API Security Top 10** threat vectors and mitigations | 16/11/2026 | 16/11/2026 | AWS Study Group |
| 3 | - Deep dive into **Cognito User Pools** vs. **Identity Pools** <br>- Implement complete user sign-up, sign-in, and refresh token lifecycle flows | 17/11/2026 | 17/11/2026 | AWS Study Group |
| 4 | - Build a custom **Lambda Authorizer** and attach it to protected API Gateway routes <br>- Configure least-privilege IAM invocation and policy generation permissions | 18/11/2026 | 18/11/2026 | AWS Study Group |
| 5 | - Upgrade **Amazon DynamoDB** table architecture: <br>&emsp; + Provision Global Secondary Indexes (GSIs) for multi-attribute queries <br>&emsp; + Harden input schema validation and standardized error handling | 19/11/2026 | 19/11/2026 | AWS Study Group |
| 6 | - Execute full end-to-end integration testing: <br>&emsp; + Client → API Gateway → Lambda Authorizer / Handler → DynamoDB → Response | 20/11/2026 | 20/11/2026 | AWS Study Group |

---

### Week 10 Key Takeaways & Achievements:

#### **1. Deepened Understanding of Token-Based Authentication & API Security**
Mastered JWT anatomy, signature verification, and the distinct roles of Access, ID, and Refresh tokens in serverless architectures. Applied OWASP API Security best practices to close common authentication and authorization gaps.

#### **2. Completed End-to-End Amazon Cognito Authentication Flows**
Configured Cognito User Pools to support user registration, sign-in, optional MFA, and automated token renewal. Validated all identity flows through AWS CLI and Postman to confirm accurate user session handling.

#### **3. Protected Routes with a Custom Lambda Authorizer**
Built and attached a custom Lambda Authorizer to verify incoming bearer tokens and return fine-grained IAM policy documents before backend handlers execute, blocking unauthorized access at the API Gateway edge.

#### **4. Optimized DynamoDB Access Patterns with Secondary Indexes**
Added Global Secondary Indexes (GSIs) to support flexible query patterns with low read latency while avoiding full-table scans. Reinforced payload validation and exception handling for predictable database operations.

#### **5. Validated Full End-to-End Backend Request Lifecycles**
Completed thorough integration testing across the entire pipeline—from client request through API Gateway authorization, Lambda execution, and DynamoDB persistence—verifying seamless interoperability across services.

#### **6. Refactored Backend Codebase for Modularity & Maintainability**
Restructured Lambda handlers using clean separation of concerns, isolating request validation, core business logic, and DynamoDB data-access layers to simplify testing and future feature expansion.

---
