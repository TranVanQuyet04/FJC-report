---
title: "Week 6 Worklog"
# date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---
<!-- {{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}} -->

### Week 6 Objectives:

* Understand and deploy FCJ Management with a scalable, highly available architecture using:
  * EC2 Auto Scaling Group (ASG)
  * Application Load Balancer (ALB)
  * Amazon RDS for the database tier
* Learn how to create an AMI and Launch Template for standardized deployments.
* Practice and compare scaling approaches (manual, scheduled, dynamic, predictive) using CloudWatch metrics.
* Clean up all resources properly to avoid unexpected charges.

### Tasks to be carried out this week:
### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Review workshop overview and target architecture (ALB + ASG + RDS) <br>- Identify required components and workflow | 10/07/2025 | 10/07/2025 | <https://000006.awsstudygroup.com/1-introduction/> |
| 3 | - Prepare environment: VPC/Subnets across multiple AZs <br>- Configure Security Groups (EC2 + RDS) <br>- Launch baseline EC2 instance (Amazon Linux 2023) | 10/08/2025 | 10/08/2025 | <https://000006.awsstudygroup.com/2-preparation/> <br><https://000006.awsstudygroup.com/2-preparation/2.1-setup-network/> <br><https://000005.awsstudygroup.com/2-prerequiste/> |
| 4 | - Create DB subnet group <br>- Launch Amazon RDS instance (MySQL) <br>- Connect from EC2 to RDS and initialize database + tables + sample data | 10/09/2025 | 10/09/2025 | <https://000006.awsstudygroup.com/2-preparation/2.3-launch-db-instance/> <br><https://000006.awsstudygroup.com/2-preparation/2.4-add-data-to-db/> |
| 5 | - Deploy FCJ Management web server on EC2 (Node.js + PM2) <br>- Configure `.env` for DB connection <br>- Verify app runs correctly on port 5000 | 10/10/2025 | 10/10/2025 | <https://000006.awsstudygroup.com/2-preparation/2.5-deploy-web-server/> |
| 6 | - Create AMI from configured EC2 and build Launch Template <br>- Create Target Group (HTTP:5000) and ALB (internet-facing) <br>- Create Auto Scaling Group and attach ALB Target Group <br>- Prepare/ upload custom metrics for Predictive Scaling in CloudWatch | 10/11/2025 | 10/11/2025 | <https://000006.awsstudygroup.com/3-create-launch-template/> <br><https://000006.awsstudygroup.com/4-setup-load-balancer/> <br><https://000006.awsstudygroup.com/6-create-auto-scaling-group/> <br><https://000006.awsstudygroup.com/2-preparation/2.6-prepare-metrics-for-predictive-scaling/> |
| 7 | - Test scaling solutions (manual / scheduled / dynamic / predictive) <br>- Observe scale-out / scale-in behavior and record results <br>- Clean up resources (ASG, ALB, TG, LT, AMI, EC2, RDS, subnet group, snapshots, etc.) | 10/12/2025 | 10/12/2025 | <https://000006.awsstudygroup.com/7-test-solutions/7.1-test-manual-scaling-solution/> <br><https://000006.awsstudygroup.com/7-test-solutions/7.2-test-scheduled-scaling-solution/> <br><https://000006.awsstudygroup.com/7-test-solutions/7.3-test-dynamic-scaling-solution/> <br><https://000006.awsstudygroup.com/7-test-solutions/7.4-test-predictive-scaling-solution/> <br><https://000006.awsstudygroup.com/8-cleanup-resources/> |


### Week 6 Achievements:

* Built understanding of a highly available and scalable AWS architecture:
  * ALB distributes HTTP traffic across instances.
  * ASG automatically adjusts capacity and improves fault tolerance by multi-AZ placement.
  * RDS provides managed relational database capabilities with network isolation via subnet groups and security groups.

* Successfully deployed FCJ Management application end-to-end:
  * Installed dependencies (Git, Node.js via nvm, PM2).
  * Configured environment variables for database connectivity.
  * Verified application accessibility through load balancer DNS (port 5000).

* Standardized instance provisioning for scaling:
  * Created AMI from a configured EC2 instance.
  * Created Launch Template to ensure repeatable instance configuration for the Auto Scaling Group.

* Implemented Load Balancing and Auto Scaling:
  * Created Target Group and configured ALB listener routing to the app tier.
  * Created ASG attached to the target group with ELB health checks and CloudWatch metrics enabled.

* Practiced and compared scaling strategies:
  * Manual scaling: useful for baseline testing but operationally inefficient.
  * Scheduled scaling: suitable for predictable traffic patterns.
  * Dynamic scaling (target tracking): responded to real-time demand using ALB request-based metrics.
  * Predictive scaling: read forecast metrics (noting UTC vs UTC+7 offset) and understood how ASG can pre-launch instances before predicted peaks.

* Completed full cleanup of workshop resources to avoid ongoing charges, including:
  * ASG, ALB, target group, launch template, AMI (and related snapshots if applicable),
  * EC2 instances, RDS instance, subnet groups, and associated networking components.
