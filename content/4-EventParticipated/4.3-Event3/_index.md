---
title: "First Cloud AI Journey: Weekly Meet Up 24/10"
date: 2026-10-24
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

### Event Overview
- **Event Name:** First Cloud AI Journey: Weekly Meet Up 24/10
- **Date:** October 24, 2026
- **Organizers:** AWS First Cloud Journey (FCJ) & AWS Study Group

---

### Technical Session Highlights

#### 1. Building Enterprise Voice AI Agents & Automated Screening Interviews
- **Speaker:** Kiet Tran (Engineer at Revve AI – AWS Partner)
- **Key Topics:**
  - Analyzed the ~200ms conversational latency benchmark and compared three Voice AI architectures: **Cascaded** (ASR → LLM → TTS), **Speech-to-Speech**, and **Full Speech-to-Speech** paired with background reasoning models.
  - Walked through the real-time call processing pipeline—spanning SIP Server, Media Server (WebRTC over UDP), Noise Canceller, and Voice Activity Detection (VAD)—achieving ~1.8s end-to-end response latency on Multi-AZ GPU infrastructure connected via AWS PrivateLink.
  - Observed a **Live Demo** of an AI recruiting assistant conducting technical screening calls on AWS fundamentals (EC2, S3, EKS, RDS, VPC), accompanied by practical lessons on normalizing Vietnamese text/abbreviations for TTS, enforcing output Guardrails, and optimizing operating costs (~3,000 VND per call).

#### 2. Multi-Account Resource Sharing & Governance with AWS Resource Access Manager (AWS RAM)
- **Speaker:** Long (AWS Study Group)
- **Key Topics:**
  - Addressed fragmented infrastructure management in **Multi-Account** environments by centrally sharing over 40 AWS resource types (VPC Subnets, Security Groups, Reserved EC2 Instances, custom AI models) via **AWS RAM** with zero sharing fees.
  - Reviewed layered access governance combining AWS RAM Permissions, IAM Policies, and AWS Organizations Service Control Policies (SCPs), backed by EventBridge alerts and CloudTrail audit logs.
  - Highlighted key Infrastructure-as-Code (Terraform/CloudFormation) practices, including mapping identical **Availability Zone IDs (AZ IDs)** across accounts to avoid cross-AZ data transfer costs and designing Hub-and-Spoke network architectures.

#### 3. Automated Security Testing with AWS Security Agent
- **Speaker:** Thinh (Engineer at Steel Solution)
- **Key Topics:**
  - Explored the three core capabilities of **AWS Security Agent**: **Design Review** (scanning Terraform code to catch architectural risks early), **Code & Security Review** (integrating directly into GitHub/GitLab Pull Requests and CI/CD pipelines), and **Automated Penetration Testing** (simulating real user workflows to map attack graphs and detect vulnerabilities in SIT/UAT environments).
  - Discussed the AWS Shared Responsibility Model and secure integration patterns using private tunnel extensions/agents to connect with self-hosted GitLab repositories without exposing source code or credentials.

#### 4. Deploying AI Agents to Production with Amazon Bedrock AgentCore
- **Speaker:** Nguyen Son An (Leader of AWS Student Group at HCMUTE)
- **Key Topics:**
  - Examined security, session isolation, and state persistence challenges when transitioning AI Agents from prototypes to production workloads.
  - Broke down **Amazon Bedrock AgentCore** across two foundational pillars:
    - **Runtime:** A serverless execution environment isolating every user session inside an independent **MicroVM** (powered by EC2 Spot Instances), billing CPU strictly during active execution.
    - **Memory:** Decoupling **Short-term Memory** (synchronous per-`sessionId` conversation history with Git-like branching) from **Long-term Memory** (asynchronous extraction of conversation summaries, user preferences, and semantic/episodic knowledge).

#### 5. Spec-Driven Development & 24/7 Autonomous Operations with Kiro
- **Speakers:** Hieu Nghi (AWS Student Group Leader) & Khoa (Tech Lead at ACB)
- **Key Topics:**
  - Introduced **Spec-Driven Development** (Plan → Design → Tasks) reinforced with built-in safety layers, including automatic secret/password redaction and mandatory human approval prior to destructive infrastructure operations.
  - Reviewed enterprise workflow demos: connecting Kiro with **Telegram** for automated 5-minute AWS database health monitoring, automating **GitHub Pull Request code reviews** against internal security and REST API standards, and managing Context Windows via auto-compact and steering file cleanup to optimize token spend.

---

### Key Takeaways & Value Gained
1. **Practical Architectural Trade-Offs:** Gained a clearer understanding of balancing latency, Vietnamese language accuracy, and infrastructure cost across GenAI/Voice AI pipelines and Multi-Account AWS setups.
2. **Shift-Left DevSecOps Mindset:** Learned how to embed automated security validation directly into IaC templates and Pull Request workflows rather than deferring security checks until post-deployment.
3. **Production-Ready Agentic Tooling:** Discovered how Amazon Bedrock AgentCore and Kiro streamline state management, session isolation, and automated development workflows on AWS.



![participate image](AWSevent3(1).jpg)
![participate image](AWSevent3(2).jpg)
![participate image](AWSevent3(3).jpg)
![participate image](AWSevent3(4).jpg)
![participate image](AWSevent3(5).jpg)
![participate image](AWSevent3(6).jpg)

