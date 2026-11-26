---
title: "Week 1 Worklog"
date: 2026-09-14
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---
### Week 1 Objectives:

- Integrate with the First Cloud Journey (FCJ) team and mentors.
- Grasp the core AWS service groups and practice navigating the AWS Management Console and CLI.

### Weekly Action Plan:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ------------------------------------------------------------------------------- |
| 2 | - Introduce myself and network with fellow FCJ interns and mentors <br> - Review internship guidelines, workflows, and workplace regulations | 14/09/2026 | 14/09/2026 | |
| 3 | - Explore core AWS service categories: <br>&emsp; + Compute <br>&emsp; + Storage <br>&emsp; + Networking <br>&emsp; + Database <br> - Practice designing AWS cloud architecture diagrams using draw.io <br> - Learn the standard workflow for completing AWS Workshops <br /><br> | 15/09/2026 | 15/09/2026 | https://cloudjourney.awsstudygroup.com/ <br> <br> https://www.youtube.com/watch?v=l8isyDe-GwY&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=2 <br> <br> https://www.youtube.com/watch?v=mXRqgMr_97U&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=3|
| 4 | - Provision a new AWS account for hands-on labs <br> - Monitor and control cloud spending using AWS Budgets <br> - Understand how to submit technical tickets via AWS Support <br> - **Hands-on Practice:** <br>&emsp; + Configure initial account security, enable MFA, and create an Admin group and user <br>&emsp; + Set up budget templates: Cost Budget, Usage Budget, RI Budget, and Savings Plans Budget <br>&emsp; + Practice switching support plans and opening a sample Support Case <br> | 16/09/2026 | 16/09/2026 | https://000001.awsstudygroup.com/ <br> <br> https://000007.awsstudygroup.com/ <br> <br> https://000009.awsstudygroup.com/ |
| 5 | - Manage user identities and permissions with AWS Identity and Access Management (AWS IAM) <br> - Build isolated network infrastructure with Amazon Virtual Private Cloud (Amazon VPC): <br>&emsp; + Network-level firewall mechanisms in VPC <br>&emsp; + Provisioning Amazon EC2 instances inside private networks <br>&emsp; + Establishing a Site-to-Site VPN connection on AWS <br> - **Hands-on Practice:** <br>&emsp; + Build a full VPC topology with Subnets, Internet Gateway, Route Tables, Security Groups, EC2 servers, NAT Gateway, and VPN connectivity | 17/09/2026 | 17/09/2026 | https://000002.awsstudygroup.com/ <br><br> https://000003.awsstudygroup.com/ |
| 6 | - Launch and host applications on Amazon Elastic Compute Cloud (Amazon EC2): <br>&emsp; + Provision a Microsoft Windows Server 2022 instance <br>&emsp; + Deploy an AWS User Management application on Amazon Linux 2 <br>&emsp; + Run a Node.js application on EC2 Windows <br>&emsp; + Enforce cost and resource governance using IAM <br> - Authorize applications to interact with AWS services via IAM Roles <br> - **Hands-on Practice:** <br>&emsp; + Connect remotely to Windows Server 2022 and Amazon Linux instances, and configure LAMP/XAMPP web stacks <br>&emsp; + Create and manage object storage using Amazon S3 buckets | 18/09/2026 | 18/09/2026 | https://000004.awsstudygroup.com/ <br><br> https://000048.awsstudygroup.com/ |

# Week 1 Key Takeaways & Achievements

## Onboarding & Alignment
- Connected with peers and mentors across the First Cloud Journey program  
- Documented key internship rules, communication channels, and milestone expectations  

## AWS Core Fundamentals
- Mapped out the architecture and use cases of the four primary AWS pillars: **Compute, Storage, Networking, and Database**  
- Built clean, standardized AWS architecture diagrams using **draw.io**  
- Adopted a structured approach to executing hands-on labs from AWS Study Group  

## Account Setup & Cost Governance
- Configured a dedicated AWS Free Tier account ready for lab environments  
- Secured root access by enabling **Multi-Factor Authentication (MFA)**  
- Implemented best-practice access separation by creating an **Admin Group** and **Admin User**  
- Configured proactive billing alerts with **AWS Budgets**:  
  - Cost Budget  
  - Usage Budget  
  - RI Budget  
  - Savings Plans Budget  
- Practiced managing support plans and creating **Support Cases** through AWS Support  

## IAM & VPC Networking
- Applied least-privilege access controls using **AWS IAM**  
- Designed and deployed a custom **Amazon VPC** infrastructure from scratch:  
  - Configured Subnets, Internet Gateway, Route Tables, and Security Groups  
  - Launched EC2 instances within isolated network tiers  
  - Provisioned a **NAT Gateway** for outbound traffic and configured a **Site-to-Site VPN**  

## EC2 & Application Hosting
- Launched and connected to both **Microsoft Windows Server 2022** and **Amazon Linux 2** instances  
- Installed and configured **LAMP** (Linux) and **XAMPP** (Windows) web server environments  
- Deployed a sample **Node.js** application on Amazon EC2  
- Attached **IAM Roles** to EC2 instances to grant secure service permissions without hardcoding credentials  
- Created and organized **Amazon S3 buckets** for object storage
