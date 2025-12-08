---
title: "Week 11 Worklog"
# date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---
<!-- {{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}} -->

### Week 11 Objectives:

* Learn and practice using **AWS CLI v2** to manage AWS resources efficiently.
* Understand AWS CLI concepts: **credentials, profiles, region, output format**, and basic troubleshooting.
* Use AWS CLI with core services: **S3, IAM, VPC, EC2** and perform proper **resource cleanup**.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 2 | - Review workshop overview “Getting Started with the AWS CLI” <br> - Understand AWS CLI, supported environments, credentials, profiles, region/output formats | 11/10/2025 | 11/10/2025 | <https://000011.awsstudygroup.com/1-introduce/> |
| 3 | - Install **AWS CLI v2** on the computer (Windows/Ubuntu) <br> - Verify installation with `aws --version` | 11/11/2025 | 11/11/2025 | <https://000011.awsstudygroup.com/3-installcli/> |
| 4 | - Configure CLI using `aws configure` (Access Key, Secret Key, region, output) <br> - Create and use multiple profiles (`--profile`) <br> - Check configurations (`aws configure list`, `list-profiles`) | 11/12/2025 | 11/12/2025 | <https://000011.awsstudygroup.com/3-installcli/> |
| 5 | - Practice viewing resources via CLI (describe/list commands) and reading outputs (`json/text/table`) <br> - Practice with **Amazon S3**: create bucket, list buckets/objects, delete object, remove bucket | 11/13/2025 | 11/13/2025 | <https://000011.awsstudygroup.com/4-infras/> <br> <https://000011.awsstudygroup.com/5-s3/> |
| 6 | - Practice with **IAM**: create group, create user, add user to group; create & delete access key <br> - Practice with **VPC**: create VPC/subnets; create/attach Internet Gateway; create route table, add route, associate route table | 11/14/2025 | 11/14/2025 | <https://000011.awsstudygroup.com/7-iam/> <br> <https://000011.awsstudygroup.com/8-network/> |
| 7 | - Create **EC2 instance using AWS CLI**: create key pair, security group, allow SSH, run instance, check public IP, SSH connect, terminate instance <br> - Read **Troubleshooting** notes for common AWS CLI errors and references <br> - Clean up resources in the correct order (SG → Subnet → Route Table → Detach IGW → Delete IGW → Delete VPC) | 11/15/2025 | 11/15/2025 | <https://000011.awsstudygroup.com/9-ec2/> <br> <https://000011.awsstudygroup.com/10-troubleshoot/> <br> <https://000011.awsstudygroup.com/11-cleanup/> |

### Week 11 Achievements:

* Installed and successfully verified **AWS CLI v2** on the computer.

* Configured AWS CLI with:
  * Access Key
  * Secret Key
  * Default Region
  * Output format  
  and understood how to work with multiple **profiles**.

* Practiced managing AWS resources via CLI and became familiar with commonly used commands for checking resources (`describe`, `list`) and reading outputs (`json/text/table`).

* Completed hands-on exercises with multiple AWS services using AWS CLI:
  * **Amazon S3**: created bucket, listed resources, deleted objects/bucket.
  * **IAM**: created group/user, managed group membership, created/deleted access keys.
  * **VPC**: created VPC & subnets, set up Internet Gateway and routing.
  * **EC2**: created key pair & security group, launched an instance, connected via SSH, and terminated the instance.

* Learned basic troubleshooting practices and performed **resource cleanup** correctly to avoid dependency errors and minimize unexpected charges.
