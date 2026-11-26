---
title: "Week 11 Worklog"
date: 2026-11-23
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives:
- Integrate the frontend application with authenticated backend API endpoints.
- Harden exception and error-handling strategies across **API Gateway** and **AWS Lambda**.
- Implement secure client-side token storage paired with automated token refresh logic.
- Build a reusable API client wrapper (Axios/Fetch) equipped with request and response interceptors.
- Enhance observability, log tracing, and performance diagnostics using **Amazon CloudWatch**.
- Complete the full-stack integration flow from UI → API Gateway → Lambda → DynamoDB.

---

### Weekly Action Plan:

| Day | Task | Start Date | Completion Date | Reference Material |
|-----|------|-------------|------------------|--------------------|
| 2 | - Connect the frontend application to **Amazon Cognito** authentication endpoints <br>- Build and refine user sign-up and sign-in UI workflows | 23/11/2026 | 23/11/2026 | AWS Study Group |
| 3 | - Implement secure token storage and automated token renewal (refresh token) flows <br>- Configure request/response interceptors inside a centralized API client wrapper | 24/11/2026 | 24/11/2026 | AWS Study Group |
| 4 | - Integrate frontend views with protected **API Gateway** routes <br>- Validate end-to-end authorization enforcement through the **Lambda Authorizer** | 25/11/2026 | 25/11/2026 | AWS Study Group |
| 5 | - Architect a unified global error-handling layer spanning both frontend and backend <br>- Standardize HTTP status codes and JSON error response payloads | 26/11/2026 | 26/11/2026 | AWS Study Group |
| 6 | - Strengthen operational visibility with **CloudWatch Logs & Metrics** <br>- Perform end-to-end debugging and latency tuning across the full stack | 27/11/2026 | 27/11/2026 | AWS Study Group |

---

### Week 11 Key Takeaways & Achievements:

#### **1. Completed Frontend Integration with Amazon Cognito**
Connected the frontend client directly to Cognito authentication endpoints, supporting seamless user registration, login, and logout flows from the UI while maintaining reliable token issuance and session state.

#### **2. Implemented Secure Token Storage & Automated Token Refresh**
Configured secure in-memory browser token handling paired with an automatic refresh mechanism upon access token expiration. Built Axios/Fetch interceptors to inject authorization headers automatically on outgoing API requests.

#### **3. Connected Frontend Views to Protected Backend APIs**
Enabled the frontend to invoke JWT-protected API Gateway routes, validating the full security chain from UI → API Client → API Gateway → Lambda → DynamoDB.

#### **4. Established a Unified Global Error-Handling System**
Standardized error payloads across Lambda handlers, aligned API Gateway gateway/integration responses, and implemented a centralized frontend error interceptor to surface clear user-facing alerts and accelerate troubleshooting.

#### **5. Enhanced Observability & Debugging with Amazon CloudWatch**
Analyzed Lambda execution logs to pinpoint latency bottlenecks and configured CloudWatch Metric Filters to track error rates and invocation durations proactively.

#### **6. Validated Complete Full-Stack Authentication & Data Flow**
Successfully executed end-to-end user workflows:  
UI → Cognito Authentication → Protected API Call → Lambda Execution → DynamoDB Persistence → UI State Update.  
All layers operated reliably with full security enforcement and structured error recovery in place.

---
