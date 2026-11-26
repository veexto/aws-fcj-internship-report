---
title: "Week 2 Worklog"
date: 2026-09-21
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---
### Week 2 Objectives:

- Master the AWS Cloud9 cloud IDE and AWS CLI to interact with and manage AWS resources programmatically.
- Dive deep into Amazon S3 features—including Static Website Hosting, Versioning, and Cross-Region Replication—paired with Amazon CloudFront for content delivery.
- Provision and administer relational databases on Amazon RDS, covering backup and disaster recovery workflows.
- Architect highly available and scalable systems using Launch Templates, Application Load Balancers (ALB), and Auto Scaling Groups (ASG).

### Weekly Action Plan:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | **Interacting with AWS Services (Cloud9 & CLI)** <br> - Provision an AWS Cloud9 development environment <br> - Explore core IDE features: terminal navigation and managing source files in the cloud <br> - Practice managing AWS services via **AWS CLI** <br> - Clean up lab resources upon completion | 21/09/2026 | 21/09/2026 | https://000049.awsstudygroup.com/ |
| 3 | **Object Storage & Content Delivery (S3 & CloudFront)** <br> - Create an S3 Bucket and upload sample assets <br> - Enable and configure **Static Website Hosting** on S3 <br> - Configure Public Access Block settings and Bucket Policies <br> - Accelerate global content delivery by integrating **Amazon CloudFront** <br> - Activate **S3 Bucket Versioning** to protect against accidental overwrites or deletions <br> - Practice object transfers and configure **Cross-Region Replication (CRR)** | 22/09/2026 | 22/09/2026 | https://000057.awsstudygroup.com/ |
| 4 | **Relational Database Administration (Amazon RDS)** <br> - Prepare network prerequisites: VPC, Security Groups for EC2 & RDS, and DB Subnet Groups <br> - Launch an Amazon EC2 instance to host the application layer <br> - Provision an **Amazon RDS** database instance in private subnets <br> - Deploy the web application and verify connectivity to RDS <br> - Execute **Backup and Restore** workflows on RDS | 23/09/2026 | 23/09/2026 | https://000005.awsstudygroup.com/ |
| 5 | **High Availability Architecture - Part 1 (Load Balancing)** <br> - Set up baseline infrastructure: VPC networking, EC2, RDS, and web server stack <br> - Build a **Launch Template** to standardize instance provisioning <br> - Configure an **Application Load Balancer (ALB)**: <br>&emsp; + Create and register a Target Group <br>&emsp; + Configure Load Balancer listeners and routing rules <br> - Verify balanced traffic distribution across backend targets | 24/09/2026 | 24/09/2026 | https://000006.awsstudygroup.com/ |
| 6 | **High Availability Architecture - Part 2 (Auto Scaling)** <br> - Create an **Auto Scaling Group (ASG)** integrated with the ALB <br> - Test and compare scaling policies: <br>&emsp; + **Manual Scaling**: Adjusting desired capacity manually <br>&emsp; + **Scheduled Scaling**: Scaling automatically on time-based schedules <br>&emsp; + **Dynamic Scaling**: Scaling dynamically based on CloudWatch metrics (e.g., CPU utilization) <br>&emsp; + **Predictive Scaling**: Reviewing load forecasts and scaling metrics <br> - Tear down all provisioned resources | 25/09/2026 | 25/09/2026 | https://000006.awsstudygroup.com/ |

# Week 2 Key Takeaways & Achievements

## Cloud Development Tools & CLI
- Set up and operated **AWS Cloud9** as a browser-based cloud IDE.
- Built fluency with **AWS CLI** commands to manage cloud infrastructure without relying on the web console.
- Streamlined the workflow of editing, debugging, and executing shell scripts directly inside Cloud9.

## Object Storage & CDN Optimization
- Hosted and served a **Static Website** directly from Amazon S3.
- Accelerated global latency and secured content delivery using **Amazon CloudFront**.
- Protected object integrity and history by enabling **S3 Versioning**.
- Configured **Cross-Region Replication (CRR)** to replicate data automatically across regions for disaster recovery.

## Relational Database Management
- Provisioned and configured a managed relational database using **Amazon RDS**.
- Connected an EC2-hosted web application securely to the backend RDS instance.
- Executed core database recovery operations, including manual **DB Snapshots** and **Point-in-Time Recovery (PITR)**.
- Isolated database network traffic using dedicated **DB Subnet Groups** and tightly scoped **Security Groups**.

## High Availability & Elasticity
- Designed a fault-tolerant architecture combining **Application Load Balancing (ALB)** and **Auto Scaling Groups (ASG)**.
- Standardized instance configurations for automated provisioning via **Launch Templates**.
- Validated multiple scaling mechanisms in practice:
  - **Manual Scaling** for direct capacity overrides.
  - **Scheduled Scaling** for predictable, recurring traffic spikes.
  - **Dynamic Scaling** to adapt automatically to real-time workload changes.
- Confirmed uninterrupted service availability and even traffic distribution throughout instance scale-out and scale-in events.
