---
title: "Week 4 Worklog"
date: 2026-10-05
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---
### Week 4 Objectives:

- Architect and deploy a production-ready **WordPress** workload engineered for High Availability (HA) and Elasticity using Auto Scaling Groups and Amazon CloudFront.
- Master **Server Migration** pipelines by importing and exporting Virtual Machines (VMs) between simulated on-premises infrastructure and AWS.
- Execute end-to-end heterogeneous **Database Migrations** utilizing AWS Schema Conversion Tool (SCT) and AWS Database Migration Service (DMS).
- Evaluate modern cloud migration services and patterns, including AWS Application Migration Service (MGN), DataSync, and Migration Hub.

### Weekly Action Plan:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | **WordPress on AWS - Part 1 (Core Deployment)** <br> - Prepare isolated network layers: VPC, Subnets, and separate Security Groups for Web and DB tiers <br> - Provision a **Multi-AZ RDS** instance to ensure database resilience and automated failover <br> - Launch an EC2 server and install the **WordPress** application stack <br> - Establish secure connectivity between WordPress on EC2 and the RDS database | 05/10/2026 | 05/10/2026 | https://000021.awsstudygroup.com/ |
| 3 | **WordPress on AWS - Part 2 (Auto Scaling & CDN)** <br> - Capture a golden **AMI** from the configured WordPress EC2 instance <br> - Configure an **Auto Scaling Group (ASG)** behind an Application Load Balancer (ALB) <br> - Accelerate static and dynamic asset delivery globally with **Amazon CloudFront** <br> - Practice database **Snapshot** creation and restoration workflows <br> - Tear down all lab resources | 06/10/2026 | 06/10/2026 | https://000021.awsstudygroup.com/ |
| 4 | **Server Migration (VM Import/Export)** <br> - Stand up a local application server to simulate an on-premises VMware environment <br> - **Import VM to AWS:** Package the local VM image, upload to S3, and convert it into an AMI/EC2 instance <br> - **Export VM from AWS:** Export a running EC2 instance back to S3 as a portable VM image <br> - Configure S3 ACLs and dedicated IAM service roles for CLI migration workflows | 07/10/2026 | 07/10/2026 | https://000014.awsstudygroup.com/ |
| 5 | **Database Migration (AWS DMS & SCT)** <br> - Build the migration sandbox: Source engine (Oracle/SQL Server) and Target engine (Amazon Aurora/RDS) <br> - Run **AWS Schema Conversion Tool (SCT)** to translate schemas and code objects across engines <br> - Configure **AWS DMS**: <br>&emsp; + Provision a Replication Instance along with Source and Target Endpoints <br>&emsp; + Execute a Migration Task combining Full Load and Change Data Capture (CDC) <br> - Explore **DMS Serverless** for automated replication capacity scaling | 08/10/2026 | 08/10/2026 | https://000043.awsstudygroup.com/ |
| 6 | **Migration Monitoring & Advanced Strategies** <br> - **DMS Observability:** Inspect CloudWatch replication metrics, Table Statistics, and Task Logs <br> - **Troubleshooting:** Diagnose memory pressure bottlenecks and table-level validation errors <br> - **Architecture Research:** Investigate enterprise migration pathways: <br>&emsp; + AWS Application Migration Service (MGN) <br>&emsp; + AWS DataSync & AWS Migration Hub <br>&emsp; + Containerizing and migrating workloads to Amazon EKS | 09/10/2026 | 09/10/2026 | https://000043.awsstudygroup.com/ <br><br> _Self-Study on AWS Migration Hub_ |

# Week 4 Key Takeaways & Achievements

## Resilient & Scalable Web Architecture
- Deployed a fault-tolerant **WordPress** architecture backed by **Multi-AZ RDS** and **Auto Scaling Groups**.
- Configured an **Application Load Balancer (ALB)** to dynamically route incoming traffic across healthy EC2 targets.
- Reduced global latency and offloaded origin traffic by placing **Amazon CloudFront** in front of the application.
- Validated disaster recovery readiness through manual **RDS Snapshots** and database restore drills.

## Server Migration & VM Portability
- Built practical proficiency with **AWS VM Import/Export** tooling and CLI commands.
- Successfully migrated a virtual machine from a simulated on-premises environment onto Amazon EC2.
- Executed the reverse workflow by exporting an active EC2 instance back into a portable VM image stored in Amazon S3.
- Configured granular IAM roles and S3 bucket permissions to authorize secure image conversion jobs.

## Heterogeneous Database Migration
- Completed a cross-engine database migration (SQL Server/Oracle to Amazon Aurora) powered by **AWS DMS**.
- Automated schema and DDL conversion between disparate database engines using the **AWS Schema Conversion Tool (SCT)**.
- Configured **Change Data Capture (CDC)** to continuously replicate ongoing transactions and minimize cutover downtime.
- Explored **DMS Serverless** to automatically provision and scale replication capacity for fluctuating workloads.
- Practiced monitoring replication health via CloudWatch metrics and troubleshooting memory contention and data-type mapping issues.
