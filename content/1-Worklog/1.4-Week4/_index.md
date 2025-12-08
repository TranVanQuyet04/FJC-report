---
title: "Week 4 Worklog"
# date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---
<!-- {{% notice warning %}}
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}} -->

### Week 4 Objectives:

* Complete **Amazon EC2 workshop (000004)** end-to-end following the flow: **networking prep → launch instances → EC2 basics → deploy app → governance → cleanup**.
* Prepare required infrastructure for the lab:
  * Create **VPCs** for **Linux** and **Windows** workloads.
  * Create **Security Groups** with **least-privilege** inbound rules for SSH/RDP/HTTP/HTTPS and application ports.
* Practice core EC2 operations:
  * Modify **instance type**
  * Create **EBS snapshots**
  * Create a **custom AMI** and launch instances from the AMI
  * Review basic **access recovery** methods (Windows/Linux)
* Deploy the sample **AWS FCJ User Management (Node.js CRUD)** application:
  * On **Linux** (LAMP + Node.js)
  * On **Windows** (XAMPP + Node.js)
* Implement **Cost & Usage Governance with IAM** (region/service/resource constraints) and perform **resource cleanup** to avoid charges.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 2 | - Read workshop overview & modules for **Amazon EC2 (000004)** | 09/24/2025 | 09/24/2025 | <http://000004.awsstudygroup.com/1-introduce/> |
| 3 | - Preparation: create **Linux VPC** + **Windows VPC** <br>- Create **Linux-SG** + **Windows-SG** (required inbound ports for lab) | 09/25/2025 | 09/25/2025 | <https://000004.awsstudygroup.com/2-prerequiste/> <br> <https://000004.awsstudygroup.com/2-prerequiste/2.1-createvpclinuxinstance/> <br> <https://000004.awsstudygroup.com/2-prerequiste/2.2-createvpcwindowsinstance/> <br> <https://000004.awsstudygroup.com/2-prerequiste/2.3-createsecuritygrouplinux/> <br> <https://000004.awsstudygroup.com/2-prerequiste/2.4-createsecuritygroupwindows/> |
| 4 | - Launch **Windows Server 2022** instance <br>- Connect to instance via **RDP** and validate access | 09/26/2025 | 09/26/2025 | <https://000004.awsstudygroup.com/3-launchwindowsinstance/> <br> <https://000004.awsstudygroup.com/3-launchwindowsinstance/3.1-createwindowssintance/> <br> <https://000004.awsstudygroup.com/3-launchwindowsinstance/3.2-connectwindowsinstance/> |
| 5 | - Launch **Amazon Linux** instance <br>- Connect via **SSH**, validate SG rules and networking | 09/27/2025 | 09/27/2025 | <https://000004.awsstudygroup.com/4-launchlinuxinstance/> <br> <https://000004.awsstudygroup.com/4-launchlinuxinstance/4.1-createlinuxinstance/> <br> <https://000004.awsstudygroup.com/4-launchlinuxinstance/4.2-connectlinuxinstance/> |
| 6 | - EC2 Basic practice: <br>&emsp; + Modify instance type <br>&emsp; + Create snapshots <br>&emsp; + Create custom AMI & launch from AMI <br>&emsp; + Review access recovery (Windows/Linux) <br>- Deploy app on **Linux** (LAMP + phpMyAdmin + Node.js CRUD) <br>- Deploy app on **Windows** (XAMPP + Node.js) <br>- Practice IAM governance policies and perform **cleanup** (terminate instances, remove AMIs/snapshots/SG/VPC/policies) | 09/28/2025 | 09/30/2025 | <https://000004.awsstudygroup.com/5-amazonec2basic/> <br> <https://000004.awsstudygroup.com/5-amazonec2basic/5.1-changeconfigureec2/> <br> <https://000004.awsstudygroup.com/5-amazonec2basic/5.2-createec2snapshot/> <br> <https://000004.awsstudygroup.com/5-amazonec2basic/5.3-createcustomami/> <br> <https://000004.awsstudygroup.com/5-amazonec2basic/5.4-launchec2ami/> <br> <https://000004.awsstudygroup.com/5-amazonec2basic/5.5-keypair-ssm-windows/> <br> <https://000004.awsstudygroup.com/5-amazonec2basic/5.6-keypair-user-data-linux/> <br> <https://000004.awsstudygroup.com/6-awsfcjmanagement-linux/> <br> <https://000004.awsstudygroup.com/6-awsfcjmanagement-linux/6.1-lampserveronec2linux/> <br> <https://000004.awsstudygroup.com/6-awsfcjmanagement-linux/6.2-setupnodejsonec2linux/> <br> <https://000004.awsstudygroup.com/6-awsfcjmanagement-linux/6.3-awsfcjmanagement/> <br> <https://000004.awsstudygroup.com/7-awsfcjmanagement-windows/> <br> <https://000004.awsstudygroup.com/7-awsfcjmanagement-windows/7.1-xampponwindows/> <br> <https://000004.awsstudygroup.com/7-awsfcjmanagement-windows/7.3-awsfcjmanagement/> <br> <https://000004.awsstudygroup.com/8-costusagegovernance/> <br> <https://000004.awsstudygroup.com/8-costusagegovernance/8.1-iamretrictregion/> <br> <https://000004.awsstudygroup.com/8-costusagegovernance/8.2-iamretrictec2family/> <br> <https://000004.awsstudygroup.com/8-costusagegovernance/8.3-iamretrictec2size/> <br> <https://000004.awsstudygroup.com/8-costusagegovernance/8.4-iamretrictecebs/> <br> <https://000004.awsstudygroup.com/8-costusagegovernance/8.5-iamretricteip/> <br> <https://000004.awsstudygroup.com/8-costusagegovernance/8.6-iamretrictetime/> <br> <https://000004.awsstudygroup.com/9-cleanup/> |

### Week 4 Achievements:

* Completed the **Amazon EC2 (000004)** workshop workflow: **Prerequisite → Launch Instances → EC2 Basic → Deploy App → Governance → Cleanup**.
* Set up the lab environment:
  * VPC + subnet/public IP settings for Linux/Windows
  * Security Groups with required ports (SSH/RDP/HTTP/HTTPS/ICMP + application port)
* Practiced core EC2 skills:
  * Changed instance type
  * Created EBS snapshots
  * Built a custom AMI and launched instances from the AMI
  * Understood basic access recovery approaches (Windows/Linux)
* Successfully deployed **AWS FCJ User Management**:
  * Linux: LAMP/MariaDB/phpMyAdmin + Node.js app and CRUD validation
  * Windows: XAMPP + Node.js deployment and functional validation
* Practiced IAM governance for cost/risk control: restricted region and EC2 constraints (family/size), plus EBS/EIP/time-based control.
* Performed full cleanup (instances/AMI/snapshots/SG/VPC/IAM policies…) to avoid unexpected charges.
