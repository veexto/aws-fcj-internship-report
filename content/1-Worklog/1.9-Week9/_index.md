---
title: "Week 9 Worklog"
date: 2026-11-09
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Objectives:
- Reinforce core backend engineering principles: RESTful API design, authentication flows, and NoSQL schema modeling.
- Build hands-on proficiency with core AWS serverless services: **Amazon API Gateway, AWS Lambda, Amazon DynamoDB, and Amazon Cognito**.
- Architect and stand up the initial v1 backend foundation for the internship project.
- Practice secure API development with standardized request validation, error handling, and response payloads.

---

### Weekly Action Plan:

| Day | Task | Start Date | Completion Date | Reference Material |
|-----|------|-------------|------------------|--------------------|
| 2 | - Study RESTful API conventions, HTTP semantics, and end-to-end backend request lifecycles <br>- Draft the initial set of API endpoints and resource schemas for the project | 09/11/2026 | 09/11/2026 | AWS Study Group |
| 3 | - Configure **Amazon API Gateway** fundamentals <br>- Define REST resources, routes, HTTP methods, request validators, and CloudWatch execution logging | 10/11/2026 | 10/11/2026 | AWS Study Group |
| 4 | - Build serverless compute handlers using **AWS Lambda** <br>- Implement and deploy core CRUD functions <br>- Validate handler execution using custom JSON test event payloads | 11/11/2026 | 11/11/2026 | AWS Study Group |
| 5 | - Model NoSQL data structures in **Amazon DynamoDB** <br>- Design table schemas with balanced partition and sort keys <br>- Connect Lambda functions to execute DynamoDB CRUD operations | 12/11/2026 | 12/11/2026 | AWS Study Group |
| 6 | - Implement user identity and access control with **Amazon Cognito** <br>- Provision a Cognito User Pool and configure sign-up/sign-in policies <br>- Attach a Cognito Authorizer to protect API Gateway routes | 13/11/2026 | 13/11/2026 | AWS Study Group |

---

### Week 9 Key Takeaways & Achievements:

#### **1. Strengthened Serverless Backend Architecture Fundamentals**
Developed a clear grasp of how decoupled, layered serverless backends operate—separating API routing, stateless business logic, identity verification, and persistence layers to achieve high scalability without server maintenance.

#### **2. Authored Initial API Specification Documentation**
Produced the v1 API contract detailing endpoint paths, request schemas, standardized JSON responses, and HTTP error codes. Establishing this specification early streamlined alignment between backend and frontend development.

#### **3. Configured Amazon API Gateway Routing & Policies**
Set up API Gateway REST routes, configured CORS headers for browser clients, enabled CloudWatch access logging, and wired proxy integrations to AWS Lambda. This clarified how external client traffic flows securely into serverless compute handlers.

#### **4. Built Core Business Logic on AWS Lambda**
Developed and deployed initial CRUD functions on AWS Lambda, gaining practical experience structuring event handlers, parsing incoming payloads, and returning well-formed HTTP status responses efficiently.

#### **5. Modeled and Queried Amazon DynamoDB Tables**
Provisioned DynamoDB tables using purposeful partition and sort key designs, practicing targeted item queries and updates while deepening understanding of NoSQL access patterns.

#### **6. Secured Endpoints with Amazon Cognito Authentication**
Created a Cognito User Pool and integrated JWT token validation directly into API Gateway via a Cognito Authorizer, ensuring protected endpoints only accept authenticated requests.

---
