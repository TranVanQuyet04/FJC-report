---
title: "Week 10 Worklog"
# date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.10. </b> "
---
<!-- {{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}} -->

### Week 10 Objectives:

* Understand **Hybrid DNS architecture** between on-premises DNS and AWS using **Route 53 Resolver**.
* Practice deploying required infrastructure with **CloudFormation / Quick Start**.
* Configure **Resolver Endpoints + Resolver Rules** and validate DNS resolution.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 2 | - Read workshop overview and key concepts: Route 53, Route 53 Resolver <br> - Understand Inbound/Outbound endpoints and Resolver rules | 11/03/2025 | 11/03/2025 | <https://000010.awsstudygroup.com/> |
| 3 | - Generate EC2 key pair for secure access (Windows password decryption) | 11/04/2025 | 11/04/2025 | <https://000010.awsstudygroup.com/2-prerequiste/2.1-createkeypair/> |
| 4 | - Deploy network infrastructure using **CloudFormation (AWS Quick Start RDGW)** <br> - Review created VPC/Subnets and stack outputs | 11/05/2025 | 11/05/2025 | <https://000010.awsstudygroup.com/2-prerequiste/2.2-launchcloudformation/> |
| 5 | - Configure Security Group (restrict ports, allow only needed access from trusted IP) | 11/06/2025 | 11/06/2025 | <https://000010.awsstudygroup.com/2-prerequiste/2.3-security/> |
| 6 | - Connect to the RDGW instance via RDP <br> - Decrypt Windows administrator password using PEM key | 11/07/2025 | 11/07/2025 | <https://000010.awsstudygroup.com/3-connecttordgw/> |
| 7 | - Deploy **AWS Managed Microsoft AD** (simulate on-premises DNS) in private subnets; record DNS IP addresses of Directory Service <br> - Create Route 53 Resolver **Outbound Endpoint** <br> - Create **Resolver Rule** to forward `onprem.example.com` to AD DNS IPs <br> - (If included in lab) Create **Inbound Endpoint** for on-prem → AWS resolution <br> - Test with `nslookup` / `Resolve-DnsName` on RDGW <br> - Cleanup: delete endpoints, disassociate & delete rules, remove Directory, delete CloudFormation stack | 11/08/2025 | 11/08/2025 | <https://000010.awsstudygroup.com/4-setupad/> <br> <https://000010.awsstudygroup.com/5-setuphyriddns/> <br> <https://000010.awsstudygroup.com/6-cleanup/> |

### Week 10 Achievements:

* Understood the idea of **Hybrid DNS** and why organizations integrate existing on-prem DNS with AWS DNS capabilities.

* Identified the 3 main building blocks of **Route 53 Resolver** for hybrid DNS:
  * **Outbound Endpoint** (AWS → on-prem DNS)
  * **Inbound Endpoint** (on-prem DNS → AWS hosted zones / VPC DNS)
  * **Resolver Rules** (conditional forwarding for specific domains)

* Successfully deployed foundational infrastructure using **CloudFormation / AWS Quick Start**, including RDGW for management access.

* Deployed **AWS Managed Microsoft AD** to simulate an on-premises DNS environment and captured Directory DNS IP addresses for forwarding targets.

* Configured DNS forwarding using:
  * Route 53 Resolver **Outbound Endpoint**
  * A **Forward rule** for `onprem.example.com`

* Validated DNS resolution on the Windows host using:
  * `nslookup onprem.example.com`
  * `Resolve-DnsName onprem.example.com`

* Completed **resource cleanup** to avoid unexpected charges by removing Route 53 Resolver resources, Directory Service, and deleting the CloudFormation stack.
