---
title: "Week 5 Worklog"
# date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---
<!-- {{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}} -->

### Week 5 Objectives:

* Understand core concepts of **Amazon RDS** (managed relational database, supported engines, storage, HA/DR, security).
* Build the required network foundation for RDS:
  * Create **VPC**, subnets across multi-AZ, and **DB Subnet Group**.
  * Create separate **Security Groups** for EC2 (app) and RDS (DB) following least privilege.
* Provision resources and validate connectivity:
  * Launch **EC2 (Amazon Linux 2023)** as an application host.
  * Create **RDS DB instance** and collect endpoint/port for application connection.
* Deploy a sample **Node.js** application and connect it to **RDS**.
* Practice **backup/restore** using RDS snapshots.
* Perform full **cleanup** to avoid ongoing AWS charges.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | ---------- | --------------- | --- |
| 2 | - Read workshop introduction & RDS overview (features, engines, backups, security) | 10/01/2025 | 10/01/2025 | <https://000005.awsstudygroup.com/1-introduce/> |
| 3 | - Complete prerequisites: <br>&emsp; + Create VPC (subnets across at least 2 AZs) <br>&emsp; + Create EC2 Security Group (HTTP/HTTPS/SSH/app port) <br>&emsp; + Create RDS Security Group (DB port only from EC2-SG) <br>&emsp; + Create DB Subnet Group | 10/02/2025 | 10/02/2025 | <https://000005.awsstudygroup.com/2-prerequiste/> <br> <https://000005.awsstudygroup.com/2-prerequiste/1-create-vpc/> <br> <https://000005.awsstudygroup.com/2-prerequiste/2-create-ec2-sg/> <br> <https://000005.awsstudygroup.com/2-prerequiste/3-create-db-sg/> <br> <https://000005.awsstudygroup.com/2-prerequiste/4-create-db-subnetgroup/> |
| 4 | - Create EC2 instance (Amazon Linux 2023) <br>- Connect to EC2 via SSH and prepare runtime (Git/Node.js dependencies) | 10/03/2025 | 10/03/2025 | <https://000005.awsstudygroup.com/3-create-ec2/> |
| 5 | - Create Amazon RDS database instance (collect Endpoint/Port/Username) <br>- Verify security group connectivity path (EC2 → RDS) | 10/04/2025 | 10/04/2025 | <https://000005.awsstudygroup.com/4-create-rds/> |
| 6 | - Deploy application: clone repo, install packages, configure `.env` to point to RDS endpoint <br>- Create database/table and insert test data <br>- Verify app runs and connects to RDS successfully <br>- Perform backup & restore via DB snapshot <br>- Cleanup resources (RDS/EC2/VPC/SG/Subnet group/snapshots/EIP/NAT if created) | 10/05/2025 | 10/06/2025 | <https://000005.awsstudygroup.com/5-deploy-app/> <br> <https://000005.awsstudygroup.com/6-backup/> <br> <https://000005.awsstudygroup.com/7-cleanup/> |

### Week 5 Achievements:

* Understood **Amazon RDS** fundamentals:
  * Managed database service for OLTP workloads, supporting engines such as Aurora, MySQL, MariaDB, PostgreSQL, Oracle, and SQL Server.
  * Key capabilities: automated backups, maintenance windows, scaling options, encryption, and network isolation via VPC.

* Completed prerequisite network and security configuration:
  * Built a dedicated **VPC** and ensured subnets span at least **two Availability Zones** to support Multi-AZ requirements.
  * Created separate **Security Groups**:
    * **EC2 SG** for web/app access and administration (restricted SSH source where applicable).
    * **RDS SG** allowing DB port access **only from EC2 SG** (not public IP ranges).

* Provisioned compute + database successfully:
  * Launched **Amazon Linux 2023 EC2** and prepared environment (Git / Node.js).
  * Created an **RDS DB instance** and confirmed endpoint/port details for application connectivity.

* Deployed and tested application with RDS:
  * Cloned the application repository, installed Node.js dependencies, configured `.env` connection variables.
  * Created database schema (DB + `user` table) and inserted sample records.
  * Verified the application works end-to-end (CRUD operations) while storing data in **RDS**.

* Practiced data protection and recovery:
  * Reviewed RDS monitoring for backups and executed **snapshot restore**, noting that restore creates a **new DB instance endpoint** which may require updating application configuration.

* Performed full cleanup to control cost:
  * Deleted DB instance, snapshots, subnet group (if created), and related network resources; terminated EC2 and removed supporting components to prevent unexpected charges.
