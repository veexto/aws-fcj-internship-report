---
title: "Week 5 Worklog"
date: 2026-10-12
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---
### Week 5 Objectives:

- **Operational Excellence:** Automate recurring operational routines (scheduled instance start/stop) using **AWS Lambda** integrated with team communication tools (Slack).
- **Monitoring & Observability:** Build advanced visual dashboards with **Grafana** connected to **Amazon CloudWatch** for deeper infrastructure telemetry.
- **Governance & Resource Organization:** Establish consistent **Tagging** standards, organize **Resource Groups**, and enforce Attribute-Based Access Control (ABAC) via **AWS IAM**.
- **Systems Management (SSM):** Practice SSH-free server administration with **Session Manager**, bulk execution via **Run Command**, and automated OS patching workflows (**Patch Manager**).
- **Infrastructure as Code (IaC):** Begin codifying and automating cloud infrastructure deployments using **AWS CloudFormation**.

### Weekly Action Plan:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | **Cost Optimization & Operational Automation** <br> - Author **AWS Lambda functions** (Python `boto3`) to automatically start and stop EC2 instances on a defined schedule <br> - Integrate Lambda with **Slack Incoming Webhooks** to dispatch real-time operational alerts <br> - Configure **Amazon EventBridge** (CloudWatch Events) rules as scheduled triggers | 12/10/2026 | 12/10/2026 | https://000022.awsstudygroup.com/ |
| 3 | **Advanced Observability with Grafana** <br> - Provision an EC2 instance to host self-managed **Grafana** (Open Source) <br> - Connect Grafana to **Amazon CloudWatch** as a native data source via IAM roles <br> - Design custom dashboards tracking EC2 CPU, Network throughput, and Disk I/O metrics | 13/10/2026 | 13/10/2026 | https://000029.awsstudygroup.com/ |
| 4 | **Resource Governance & Security (Tags & IAM ABAC)** <br> - **Tagging Strategy:** Enforce standardized metadata tags across resources (`Env`, `Owner`, `CostCenter`) <br> - Create **Resource Groups** to query and manage workloads sharing common tags <br> - **ABAC Implementation:** Author IAM Policies restricting EC2 actions to instances whose tags match the requesting user's principal tags | 14/10/2026 | 14/10/2026 | https://000027.awsstudygroup.com/ <br><br> https://000028.awsstudygroup.com/ |
| 5 | **Systems Administration with AWS Systems Manager (SSM)** <br> - **Session Manager:** Connect securely to public and private instances without open SSH ports or Bastion Hosts (Port Forwarding and S3 Session Audit Logs) <br> - **Run Command:** Execute administrative scripts remotely across a fleet of instances <br> - *Conceptual Review:* Walk through **Patch Manager** scanning and compliance baselines | 15/10/2026 | 15/10/2026 | https://000058.awsstudygroup.com/ <br><br> https://000031.awsstudygroup.com/ |
| 6 | **Infrastructure as Code (AWS CloudFormation)** <br> - Author foundational **CloudFormation templates** (YAML/JSON) to provision VPC and EC2 resources <br> - Master core template constructs: **Stacks**, **Parameters**, **Mappings**, and **Outputs** <br> - Run **Drift Detection** to uncover out-of-band manual configuration changes | 16/10/2026 | 16/10/2026 | https://000037.awsstudygroup.com/ |

# Week 5 Key Takeaways & Achievements

## Automation & Cloud Cost Control
- Implemented an **automated cost-saving workflow** using **AWS Lambda** to power down non-production EC2 instances outside working hours.
- Built real-time operational visibility by routing Lambda execution notifications directly into a dedicated **Slack channel**.
- Eliminated manual scheduling overhead by leveraging **EventBridge Rules** to trigger serverless automation reliably.

## Custom Monitoring & Visualization
- Deployed and configured a self-hosted **Grafana** server running on Amazon EC2.
- Integrated **Amazon CloudWatch** as a data source, enabling richer, customizable metric visualizations beyond standard console graphs.
- Built tailored dashboards to track EC2 fleet health and resource utilization trends.

## Resource Governance & Attribute-Based Security
- Established structured **Tagging conventions** to categorize cloud assets by environment (`Dev`/`Prod`), ownership, and cost center.
- Leveraged **Resource Groups** to organize and manage related resources in bulk.
- Strengthened access isolation through **Attribute-Based Access Control (ABAC)**: crafted IAM policies allowing engineers to manage only those EC2 instances matching their department tags.

## Modern Systems Operations (SysOps)
- Eliminated exposed SSH ports, key pairs, and Bastion Hosts by adopting **AWS Systems Manager Session Manager** for encrypted shell access.
- Configured automated **Session Logging** to Amazon S3 to satisfy security auditing and compliance requirements.
- Studied end-to-end **Patch Manager** workflows for automating OS patch baselines and compliance reporting across instance fleets.
- Used **Run Command** to broadcast configuration updates across multiple servers simultaneously without individual logins.

## Infrastructure as Code (IaC)
- Shifted from manual console provisioning to declarative infrastructure definitions using **AWS CloudFormation**.
- Deployed repeatable CloudFormation Stacks to stand up VPC networking and EC2 compute resources consistently.
- Practiced **Drift Detection** to audit live environments and identify discrepancies against declared template states.
