---
title: "Week 7 Worklog"
date: 2026-10-26
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---
### Week 7 Objectives:

- **Application Containerization:** Master packaging workloads with **Docker** and managing container images centrally in Amazon ECR.
- **Container Orchestration:** Deploy and operate scalable containerized services on **Amazon ECS (Elastic Container Service)**.
- **DevOps & CI/CD Automation:** Build automated **CI/CD Pipelines** (AWS CodePipeline, CodeBuild, CodeDeploy) for streamlined deployments across EC2 and ECS.
- **Hybrid Storage Integration:** Bridge on-premises storage protocols with AWS cloud storage using **AWS Storage Gateway (File Gateway)** and **Amazon FSx for Windows File Server**.
- **Advanced NoSQL Architecture:** Deep dive into **Amazon DynamoDB** data modeling patterns, indexing strategies, and throughput tuning for high-performance workloads.

### Weekly Action Plan:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | **Application Containerization (Docker & ECR)** <br> - Install Docker Engine on local workstations and Amazon EC2 <br> - Author Dockerfiles to containerize sample Frontend and Backend services <br> - Use **Docker Compose** to orchestrate multi-container local stacks <br> - Tag and push container images to **Amazon ECR** (Elastic Container Registry) | 26/10/2026 | 26/10/2026 | https://000015.awsstudygroup.com/ |
| 3 | **Container Orchestration (Amazon ECS)** <br> - Provision an **ECS Cluster** supporting both Fargate and EC2 launch types <br> - Author **Task Definitions** and configure ECS Services for desired task counts <br> - Attach an **Application Load Balancer (ALB)** for dynamic traffic routing <br> - Configure internal **Service Discovery** via **AWS Cloud Map** | 27/10/2026 | 27/10/2026 | https://000016.awsstudygroup.com/ |
| 4 | **CI/CD Pipelines for Containers** <br> - Configure **AWS CodePipeline** triggered automatically by GitHub/GitLab commits <br> - Set up **AWS CodeBuild** projects to compile, build, and push Docker images to ECR <br> - Automate zero-downtime rolling deployments to ECS Clusters <br> - Enable **CloudWatch Container Insights** for telemetry and **FireLens** for log routing | 28/10/2026 | 28/10/2026 | https://000017.awsstudygroup.com/ |
| 5 | **CI/CD for EC2 & Hybrid Cloud Storage** <br> - **CodePipeline for EC2:** Automate application deployments via the AWS CodeDeploy agent <br> - **AWS Storage Gateway:** Configure a File Gateway to expose S3 buckets as standard NFS file shares <br> - **Amazon FSx:** Provision a fully managed **FSx for Windows File Server** and mount shares over SMB | 29/10/2026 | 29/10/2026 | https://000023.awsstudygroup.com/ <br><br> _Self-Study on FSx & Storage Gateway_ |
| 6 | **Advanced Amazon DynamoDB Architecture** <br> - **Data Modeling:** Apply **Single Table Design** principles for relational-style access patterns <br> - **Performance Tuning:** Design balanced Partition Keys, Sort Keys, and provision RCU/WCU capacity <br> - **Advanced Capabilities:** Implement Global Secondary Indexes (GSI), DynamoDB Streams, and Global Tables | 30/10/2026 | 30/10/2026 | https://000039.awsstudygroup.com/ |

# Week 7 Key Takeaways & Achievements

## Containerization & Orchestration
- Packaged a monolithic application into portable **Docker images**, decoupling application dependencies from host OS configurations.
- Deployed a resilient container cluster on **Amazon ECS**, enforcing compute and memory boundaries via Task Definitions.
- Configured **Service Discovery** with AWS Cloud Map so microservices communicate reliably via logical DNS names rather than ephemeral container IPs.
- Integrated an **Application Load Balancer** to route external HTTP traffic across dynamically scaling container tasks.

## DevOps & Automated CI/CD
- Engineered an end-to-end **CI/CD Pipeline** leveraging AWS CodePipeline and CodeBuild.
- Enabled **Continuous Deployment**, where Git repository commits automatically trigger image builds and rolling updates on ECS with zero service interruption.
- Implemented granular container observability with **CloudWatch Container Insights** to monitor task-level CPU and memory utilization.
- Centralized container log streams using **FireLens** to simplify debugging and log analytics.

## Hybrid Cloud Storage Integration
- Bridged legacy on-premises file protocols with scalable cloud object storage.
- Deployed **File Storage Gateway**, enabling existing applications to read and write data to Amazon S3 over standard NFS mounts.
- Provisioned **Amazon FSx for Windows File Server**, delivering native SMB file shares backed by Active Directory integration.

## High-Performance NoSQL Database Design
- Strengthened NoSQL modeling proficiency with **Amazon DynamoDB**.
- Improved query latency and partition distribution by selecting high-cardinality Partition Keys and composite Sort Keys.
- Leveraged **Global Secondary Indexes (GSI)** to support secondary query patterns without duplicating primary table records.
- Explored **DynamoDB Streams** to power event-driven workflows that invoke AWS Lambda functions on item mutations.
