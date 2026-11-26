---
title: "Week 8 Worklog"
date: 2026-11-02
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:

- **Cost Optimization:** Master commitment-based discount models such as **Savings Plans** and **Reserved Instances (RI)** across EC2 and Amazon RDS.
- **Resource Right-Sizing:** Leverage **AWS Compute Optimizer** alongside the CloudWatch Agent to evaluate real workload utilization and adjust instance sizing.
- **Cloud Financial Management (FinOps):** Analyze granular spending trends using **AWS Cost Explorer** and audit inter-service/internet data transfer charges.
- **Midterm Knowledge Assessment:** Complete a timed practice exam modeled after the **AWS Certified Solutions Architect - Associate (SAA-C03)** certification.

### Weekly Action Plan:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | **Commitment-Based Cost Saving Models** <br> - Compare and contrast **Savings Plans** (Compute vs. EC2 Instance) and **Reserved Instances (RI)** <br> - Analyze automated Savings Plan Recommendations based on historical usage <br> - Practice the purchasing workflow for Savings Plans and Reserved DB Instances | 02/11/2026 | 02/11/2026 | https://000042.awsstudygroup.com/ |
| 3 | **Resource Optimization & Right-Sizing** <br> - Install and configure the **CloudWatch Agent** on EC2 to collect OS-level memory (RAM) metrics <br> - Attach IAM Roles granting metric ingestion and telemetry access to CloudWatch and Compute Optimizer <br> - Review **AWS Compute Optimizer** findings to identify over-provisioned instances and optimal instance families <br> - Apply EC2 performance-to-cost optimization best practices | 03/11/2026 | 03/11/2026 | https://000032.awsstudygroup.com/ |
| 4 | **Cost Visualization & Spend Analysis** <br> - Use **AWS Cost Explorer** to break down expenditures by Service and Linked Account <br> - Track **Coverage** and **Utilization** metrics for active Savings Plans and RIs <br> - Evaluate infrastructure **Elasticity** across peak and off-peak operating windows | 04/11/2026 | 04/11/2026 | https://000034.awsstudygroup.com/ |
| 5 | **Advanced Spend Analytics & Curriculum Review** <br> - Build tailored **Custom Reports** isolating EC2 compute and storage expenses <br> - Audit **Data Transfer** charges (cross-AZ, cross-region, and internet egress) <br> - *Conceptual Research:* Explore configuring **AWS Cost & Usage Reports (CUR)** and querying billing datasets via **Amazon Athena** <br> - Consolidate core concepts from the first 8 weeks ahead of the midterm assessment | 05/11/2026 | 05/11/2026 | https://000034.awsstudygroup.com/ <br><br> _SAA-C03 Curriculum Review_ |
| 6 | **Midterm Assessment Exam** <br> - Take a full-length **AWS Certified Solutions Architect - Associate (SAA-C03)** simulation exam <br> - Exam format: 65 scenario-based multiple-choice questions / 130 minutes <br> - Core domains tested: IAM, VPC, EC2, S3, RDS, High Availability/Auto Scaling, and Cost Optimization <br> - Score results, review explanations, and map out knowledge gaps for targeted study | 06/11/2026 | 06/11/2026 | _AWS SAA-C03 Practice Exam_ |

# Week 8 Key Takeaways & Achievements

## Cloud Cost Optimization Strategy
- Distinguished between **Savings Plans** (flexible hourly spend commitments) and **Reserved Instances** (capacity/instance-specific discounts) to match pricing models with workload predictability.
- Learned to interpret **AWS Recommendations** to size commitment levels accurately without risking under-utilization.
- Practiced applying Reserved Instances to **Amazon RDS** databases to lower steady-state operational costs.

## Compute & System Right-Sizing
- Deployed the **CloudWatch Agent** to capture guest OS memory metrics missing from default hypervisor telemetry, enabling accurate instance profiling.
- Used **AWS Compute Optimizer** to pinpoint over-provisioned and under-provisioned EC2 instances and execute informed right-sizing decisions.

## Cloud Financial Management (FinOps)
- Built fluency in **AWS Cost Explorer** to track daily and monthly spend trajectories across individual AWS services.
- Created **Custom Reports** specifically targeting **Data Transfer** expenses—an often-overlooked cost driver in distributed architectures.
- Learned to evaluate the ROI of existing commitments using **Coverage** and **Utilization** dashboards.

## Competency Benchmark (Midterm)
- Completed a timed **AWS Certified Solutions Architect - Associate** practice exam under test conditions.
- Reinforced core architectural principles across the four primary pillars: **Compute, Storage, Networking, and Database**.
- Pinpointed specialized topics—such as complex Hybrid Cloud connectivity and advanced VPC routing—to prioritize during the second half of the internship.
