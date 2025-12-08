---
title: "Week 3 Worklog"
# date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---
<!-- {{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}} -->


### Week 3 Objectives:

* Practice AWS Networking with VPC and Site-to-Site VPN.
* Understand VPN components (VPG / CGW / 2 tunnels) and routing (Static vs BGP).
* Learn monitoring + troubleshooting flow (IKE → IPsec → Tunnel → Routing).
* Perform cleanup to avoid unexpected costs.
* Get exposure to IaC (CloudFormation / CDK / Terraform).

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | ---------- | --------------- | --- |
| 2 | - Read workshop: Amazon VPC and AWS Site-to-Site VPN (overview + lab scope) <br> - Understand architecture: VPC ASG (Main office) & VPC ASG VPN (Branch office) and goal (private IP connectivity) | 09/17/2025 | 09/17/2025 | <https://000003.awsstudygroup.com/5-vpnsitetosite/> |
| 3 | - Create Branch environment: ASG VPN VPC `10.11.0.0/16` <br> - Create subnet **VPN Public** `10.11.1.0/24` (ap-southeast-1a) + enable auto-assign public IPv4 <br> - Create + attach **Internet Gateway** <br> - Create route table **VPN - Public**, add `0.0.0.0/0 → IGW`, associate with VPN Public subnet | 09/18/2025 | 09/18/2025 | <https://000003.awsstudygroup.com/5-vpnsitetosite/5.1-createvpnenv/> <br><https://000003.awsstudygroup.com/5-vpnsitetosite/5.1-createvpnenv/5.1.1-createvpnvpc/> |
| 4 | - Create security group **VPN Public - SG**: allow SSH (My IP), ICMP, UDP `500/4500` (IPsec) <br> - Launch **Customer Gateway EC2 instance** in ASG VPN VPC (public subnet) and verify SSH connection | 09/19/2025 | 09/19/2025 | <https://000003.awsstudygroup.com/5-vpnsitetosite/5.1-createvpnenv/5.1.2-createec2vpn/> |
| 5 | - Create **Virtual Private Gateway (VPG)** and attach to **VPC ASG** <br> - Create **Customer Gateway (CGW)** using public IP of Customer Gateway EC2 <br> - Create **Site-to-Site VPN Connection** (Static routing, prefix `10.11.0.0/16`) <br> - Enable **route propagation** on related route tables (public + private) | 09/20/2025 | 09/20/2025 | <https://000003.awsstudygroup.com/5-vpnsitetosite/5.2-vpnsitetosite/> <br><https://000003.awsstudygroup.com/5-vpnsitetosite/5.2-vpnsitetosite/5.2.1-createvpgw/> <br><https://000003.awsstudygroup.com/5-vpnsitetosite/5.2-vpnsitetosite/5.2.2-createcustomergw/> <br><https://000003.awsstudygroup.com/5-vpnsitetosite/5.2-vpnsitetosite/5.2.3-createvpnconnection/> |
| 6 | - Download VPN configuration from AWS (OpenSwan/StrongSwan profile) <br> - Configure Customer Gateway software (OpenSwan / Libreswan / StrongSwan depending on OS) <br> - Configure sysctl IP forwarding + IPsec config/secrets for **2 tunnels**, start services <br> - Validate private connectivity: ping between Customer Gateway ↔ EC2 Private via private IP | 09/21/2025 | 09/21/2025 | <https://000003.awsstudygroup.com/5-vpnsitetosite/5.2-vpnsitetosite/5.2.4-configurecustomergw/> <br><https://000003.awsstudygroup.com/5-vpnsitetosite/5.2-vpnsitetosite/5.2.7-troubleshootingguide/> |
| 7 | - Modify AWS VPN tunnel options (verify both tunnels UP) <br> - Enable **Tunnel activity log** to CloudWatch and review log streams <br> - Practice troubleshooting flow: **IKE → IPsec → Tunnel → Routing** (check status, logs, routes, firewall rules) <br> - Review alternative configurations: StrongSwan (IKEv2), BGP (dynamic routing), Transit Gateway (optional) | 09/22/2025 | 09/22/2025 | <https://000003.awsstudygroup.com/5-vpnsitetosite/5.2-vpnsitetosite/5.2.5-modifyvpn/> <br><https://000003.awsstudygroup.com/5-vpnsitetosite/5.2-vpnsitetosite/5.2.6-alternativeconfigurations/> <br><https://000003.awsstudygroup.com/5-vpnsitetosite/5.2-vpnsitetosite/5.2.7-troubleshootingguide/> <br><http://000003.awsstudygroup.com/5-vpnsitetosite/5.2-vpnsitetosite/5.2.8-awsofficialtroubleshooting/> <br><https://000003.awsstudygroup.com/5-vpnsitetosite/5.3-vpnsitetosite-optional/> |
| 8 | - Cleanup resources to avoid cost: terminate EC2, delete NAT Gateway + release EIP, delete endpoints <br> - Delete VPN resources in order: VPN connection → VPG → CGW → VPCs/related components <br> - Read IaC templates and deployment approaches (CloudFormation / CDK / Terraform) | 09/23/2025 | 09/23/2025 | <https://000003.awsstudygroup.com/6-cleanup/> <br><https://000003.awsstudygroup.com/7-infrastructureascode/> |

### Week 3 Achievements:

* Built a branch “on-premises emulator” environment (ASG VPN VPC + public subnet + IGW + routing) to support Site-to-Site VPN lab testing.
* Successfully set up AWS Site-to-Site VPN core components:
  * Virtual Private Gateway (VPG) attached to VPC ASG
  * Customer Gateway (CGW) using EC2 public IP
  * Site-to-Site VPN connection with **2 tunnels** for high availability
  * Static routing configuration and route propagation on VPC route tables
* Configured the Customer Gateway instance (OpenSwan/Libreswan/StrongSwan) and verified **private IP connectivity** across the VPN tunnel.
* Practiced monitoring and troubleshooting with CloudWatch tunnel logs and a structured workflow:
  * **IKE → IPsec → Tunnel → Routing** checks (status, logs, firewall rules, route tables)
* Completed cleanup of lab resources (EC2/NAT/EIP/VPN/VPC components) to prevent unexpected charges.
* Got exposure to Infrastructure as Code (IaC) approaches and sample templates:
  * CloudFormation, AWS CDK, Terraform.
