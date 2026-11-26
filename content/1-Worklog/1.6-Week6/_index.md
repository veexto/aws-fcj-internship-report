---
title: "Week 6 Worklog"
date: 2026-10-19
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---
### Week 6 Objectives:

- **Identity & Access Management (IAM):** Establish centralized authentication via **IAM Identity Center (SSO)**, cap maximum effective privileges with **Permission Boundaries**, and tighten role assumption/passing using conditional IAM policies.
- **Security Compliance & Edge Defense:** Automate security posture assessments with **AWS Security Hub** and shield web workloads using **AWS WAF**.
- **Data Protection & Resilience:** Control cryptographic keys with **AWS KMS** alongside CloudTrail/Athena auditing, and standardize centralized backup policies with **AWS Backup**.
- **Enterprise Network Topologies:** Architect inter-VPC connectivity using point-to-point **VPC Peering** and scalable hub-and-spoke **AWS Transit Gateway** designs.

### Weekly Action Plan:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | **Advanced Identity & Privilege Governance** <br> - Configure **IAM Identity Center (SSO)** to centralize user authentication across AWS accounts <br> - Author **Permission Boundaries** to cap maximum allowable permissions for delegated IAM users and roles <br> - Enforce **IAM Role Conditions** (such as `iam:PassedToService`) to prevent unauthorized role-passing abuse | 19/10/2026 | 19/10/2026 | https://000012.awsstudygroup.com/ <br><br> https://000030.awsstudygroup.com/ <br><br> https://000044.awsstudygroup.com/ |
| 3 | **Security Posture & Web Application Defense** <br> - Enable **AWS Security Hub** to run automated compliance checks against CIS benchmarks <br> - Deploy **AWS WAF** at the application edge: <br>&emsp; + Build Web ACLs layered with AWS Managed Rule Groups <br>&emsp; + Block SQL Injection and XSS exploit payloads ahead of the Application Load Balancer | 20/10/2026 | 20/10/2026 | https://000018.awsstudygroup.com/ <br><br> https://000026.awsstudygroup.com/ |
| 4 | **Data Encryption & Centralized Backup (KMS & AWS Backup)** <br> - Provision Customer Managed Keys (CMK) inside **AWS KMS** for granular key lifecycle control <br> - Enforce server-side encryption on S3 buckets and audit key usage via **CloudTrail** & **Amazon Athena** <br> - Configure **AWS Backup**: <br>&emsp; + Create an encrypted Backup Vault and scheduled Backup Plan <br>&emsp; + Execute on-demand backup jobs and perform full resource recovery drills | 21/10/2026 | 21/10/2026 | https://000033.awsstudygroup.com/ <br><br> https://000013.awsstudygroup.com/ |
| 5 | **Inter-VPC Connectivity & Hub-and-Spoke Networking** <br> - **VPC Peering:** Establish private peering connections between isolated VPCs and update Route Tables and DNS resolution <br> - **AWS Transit Gateway (TGW):** Deploy a central routing hub interconnecting multiple VPCs <br> - Segment **TGW Route Tables** to isolate traffic flows between distinct network environments | 22/10/2026 | 22/10/2026 | https://000019.awsstudygroup.com/ <br><br> https://000020.awsstudygroup.com/ |
| 6 | **Security Audit & Resource Teardown** <br> - Audit all deployed IAM policies, WAF rules, and KMS key configurations <br> - **Cost Cleanup:** Delete Transit Gateway attachments/gateways, NAT Gateways, and disable Security Hub/AWS Config to avoid ongoing charges <br> - Schedule deletion for customer-managed KMS keys | 23/10/2026 | 23/10/2026 | _All Lab Cleanup Sections_ |

# Week 6 Key Takeaways & Achievements

## Identity & Access Governance (IAM)
- Deployed **IAM Identity Center** to streamline single sign-on (SSO) and centralize workforce access management.
- Applied **Permission Boundaries** to mitigate privilege escalation risks, ensuring delegated administrators cannot grant permissions beyond defined guardrails.
- Hardened role delegation by embedding **Condition keys** into IAM policies to restrict which AWS services and principals can assume or pass specific roles.

## Compliance Monitoring & Application Defense
- Activated **AWS Security Hub** to aggregate security findings and continuously evaluate infrastructure against the **CIS AWS Foundations Benchmark**.
- Protected public-facing web endpoints with **AWS WAF**, configuring rules that filter out SQL Injection, XSS attempts, and malicious IP traffic before reaching the Application Load Balancer.

## Cryptographic Controls & Disaster Recovery
- Secured sensitive S3 data at rest using **Customer Managed Keys (CMK)** in **AWS KMS**.
- Built an auditable key-usage trail by capturing KMS API events in **AWS CloudTrail** and querying logs with **Amazon Athena**.
- Standardized Disaster Recovery (DR) operations with **AWS Backup**, automating EBS volume backup schedules and verifying point-in-time restoration from recovery points.

## Scalable Enterprise Networking
- Established private, low-latency communication between isolated VPCs via **VPC Peering**, keeping internal traffic off the public internet.
- Eliminated complex full-mesh peering overhead by architecting a scalable hub-and-spoke network topology with **AWS Transit Gateway**.
- Configured segmented **Route Tables** across both VPCs and Transit Gateway to enforce strict traffic routing and environment isolation.
