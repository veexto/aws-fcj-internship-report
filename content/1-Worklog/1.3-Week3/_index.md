---
title: "Week 3 Worklog"
date: 2026-09-28
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---
### Week 3 Objectives:

- Establish end-to-end monitoring and observability pipelines with **Amazon CloudWatch** (Metrics, Logs, Alarms, and Dashboards).
- Architect a **Hybrid DNS** topology bridging on-premises networks with AWS via **Route 53 Resolver** and Microsoft Active Directory.
- Build fluency in **AWS CLI** to automate resource provisioning and management across Storage, Networking, Identity, and Compute layers.

### Weekly Action Plan:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | **Monitoring & Observability (Amazon CloudWatch)** <br> - Configure **CloudWatch Metrics**: inspecting metrics, search expressions, and math expressions <br> - Query and filter application logs using **CloudWatch Logs Insights** & Metric Filters <br> - Set up **CloudWatch Alarms** for proactive threshold alerting <br> - Build unified **CloudWatch Dashboards** for real-time visibility <br> - **Hands-on Practice:** Visualize EC2 instance performance and trigger alerts on high CPU utilization | 28/09/2026 | 28/09/2026 | https://000008.awsstudygroup.com/ |
| 3 | **Hybrid Connectivity & DNS Resolution** <br> - Deploy **Microsoft Active Directory (AD)** on AWS <br> - Configure **Remote Desktop Gateway (RDGW)** for secure administrative access <br> - Implement **Hybrid DNS** with Route 53 Resolver: <br>&emsp; + Provision Inbound and Outbound Resolver Endpoints <br>&emsp; + Configure Conditional Forwarding Rules <br> - Validate bidirectional DNS resolution between simulated on-premises and AWS environments | 29/09/2026 | 29/09/2026 | https://000010.awsstudygroup.com/ |
| 4 | **AWS CLI Mastery - Part 1 (Setup & Storage)** <br> - Install and configure **AWS CLI v2** credentials and profiles <br> - **S3 Automation:** Manage buckets and execute multipart uploads via CLI <br> - **Messaging:** Provision and manage **Amazon SNS** topics and subscriptions from the terminal <br> - Utilize CLI output formats (`json`, `table`, `text`) and JMESPath `--query` filtering | 30/09/2026 | 30/09/2026 | https://000011.awsstudygroup.com/ <br><br> https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-troubleshooting.html |
| 5 | **AWS CLI Mastery - Part 2 (Compute & Networking)** <br> - **IAM Security:** Manage users, roles, and execute `sts assume-role` workflows via CLI <br>&emsp; + Authenticate sessions using MFA tokens in the CLI <br> - **Network Infrastructure:** Provision VPCs, Subnets, and Internet Gateways purely via CLI commands <br> - **Compute:** Launch and configure **EC2 instances** from the command line | 01/10/2026 | 01/10/2026 | https://000011.awsstudygroup.com/ <br><br> [Deep Dive: AWS Command Line Interface](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html) |
| 6 | **AWS CLI Mastery - Part 3 (Troubleshooting & Cleanup)** <br> - **Troubleshooting:** Diagnose and resolve common CLI errors (credential conflicts, IAM permission denials, malformed parameters) <br> - **Advanced Authentication:** Cache and manage SAML federated credentials <br> - Execute full environment cleanup via CLI scripts to prevent lingering charges | 02/10/2026 | 02/10/2026 | https://000011.awsstudygroup.com/ <br><br> [AWS re:Invent 2019: Introduction to the AWS CLI v2](https://www.youtube.com/watch?v=k_l8k2A8F_k) |

# Week 3 Key Takeaways & Achievements

## Observability & System Monitoring
- Deployed a centralized monitoring pipeline powered by **Amazon CloudWatch**.
- Built custom **Dashboards** to track critical operational metrics (CPU, Memory, Disk I/O) in real time.
- Configured **CloudWatch Alarms** integrated with Amazon SNS to dispatch automated notifications upon threshold breaches.
- Applied **CloudWatch Logs Insights** queries to parse and troubleshoot application log streams efficiently.

## Hybrid Networking & DNS
- Architected and deployed a **Hybrid DNS** solution linking simulated on-premises infrastructure with AWS.
- Provisioned **Microsoft Active Directory** on AWS and integrated directory DNS with Route 53.
- Configured **Route 53 Resolver Endpoints** (Inbound/Outbound) and **Forwarding Rules** for seamless cross-environment name resolution.
- Verified secure administrative connectivity through **Remote Desktop Gateway (RDGW)**.

## Command-Line Infrastructure Management (AWS CLI)
- Transitioned daily operations from manual console clicks to reproducible **AWS CLI** workflows.
- Automated provisioning across core AWS service layers:
  - **Storage:** Created S3 buckets and handled large object transfers via multipart uploads.
  - **Security:** Administered IAM users and policies, and practiced **Assuming Roles** for temporary privilege elevation.
  - **Networking:** Built a complete VPC network stack (VPC, Subnets, IGW, Route Tables) using CLI scripts.
  - **Compute:** Launched EC2 instances bootstrapped with `user-data` scripts from the command line.
- Strengthened troubleshooting skills around CLI profiles, MFA/SAML session tokens, and AWS API error diagnostics.
