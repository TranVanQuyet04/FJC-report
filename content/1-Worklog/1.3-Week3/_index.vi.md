---
title: "Worklog Tuần 3"
# date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---
<!-- {{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}} -->


### Mục tiêu tuần 3:

* Thực hành AWS Networking với VPC và Site-to-Site VPN.
* Hiểu các thành phần của VPN (VPG / CGW / 2 tunnels) và định tuyến (Static vs BGP).
* Nắm được luồng monitoring + troubleshooting (IKE → IPsec → Tunnel → Routing).
* Thực hiện cleanup để tránh phát sinh chi phí ngoài ý muốn.
* Làm quen Infrastructure as Code (CloudFormation / CDK / Terraform).

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | ------------ | --------------- | --- |
| 2 | - Đọc workshop **Amazon VPC and AWS Site-to-Site VPN** (tổng quan + phạm vi lab) <br> - Nắm kiến trúc: **VPC ASG (Main office)** và **VPC ASG VPN (Branch office)**, mục tiêu là **kết nối private IP** giữa 2 môi trường | 17/09/2025 | 17/09/2025 | <https://000003.awsstudygroup.com/5-vpnsitetosite/> |
| 3 | - Tạo môi trường Branch: **ASG VPN VPC** `10.11.0.0/16` <br> - Tạo subnet **VPN Public** `10.11.1.0/24` (ap-southeast-1a) và bật auto-assign public IPv4 <br> - Tạo và attach **Internet Gateway** <br> - Tạo route table **VPN - Public**, thêm route `0.0.0.0/0 → IGW`, associate với subnet VPN Public | 18/09/2025 | 18/09/2025 | <https://000003.awsstudygroup.com/5-vpnsitetosite/5.1-createvpnenv/> <br><https://000003.awsstudygroup.com/5-vpnsitetosite/5.1-createvpnenv/5.1.1-createvpnvpc/> |
| 4 | - Tạo security group **VPN Public - SG**: SSH (My IP), ICMP, UDP `500/4500` (IPsec/NAT-T) <br> - Launch EC2 **Customer Gateway instance** trong ASG VPN VPC (public subnet) và kiểm tra SSH vào instance | 19/09/2025 | 19/09/2025 | <https://000003.awsstudygroup.com/5-vpnsitetosite/5.1-createvpnenv/5.1.2-createec2vpn/> |
| 5 | - Tạo **Virtual Private Gateway (VPG)** và attach vào **VPC ASG** <br> - Tạo **Customer Gateway (CGW)** bằng public IP của EC2 Customer Gateway <br> - Tạo **Site-to-Site VPN Connection** (Static routing, prefix `10.11.0.0/16`) <br> - Enable **route propagation** trên các route table liên quan (public + private) | 20/09/2025 | 20/09/2025 | <https://000003.awsstudygroup.com/5-vpnsitetosite/5.2-vpnsitetosite/5.2.1-createvpgw/> <br><https://000003.awsstudygroup.com/5-vpnsitetosite/5.2-vpnsitetosite/5.2.2-createcustomergw/> <br><https://000003.awsstudygroup.com/5-vpnsitetosite/5.2-vpnsitetosite/5.2.3-createvpnconnection/> |
| 6 | - Download VPN configuration từ AWS (profile OpenSwan/StrongSwan) <br> - Cấu hình CGW software (OpenSwan/Libreswan/StrongSwan tuỳ OS) <br> - Cấu hình sysctl (IP forwarding), cấu hình IPsec cho **2 tunnels**, start service <br> - Kiểm tra kết nối: ping private IP giữa Customer Gateway ↔ EC2 Private | 21/09/2025 | 21/09/2025 | <https://000003.awsstudygroup.com/5-vpnsitetosite/5.2-vpnsitetosite/5.2.4-configurecustomergw/> <br><https://000003.awsstudygroup.com/5-vpnsitetosite/5.2-vpnsitetosite/5.2.7-troubleshootingguide/> |
| 7 | - Modify VPN tunnel options (xác nhận 2 tunnels UP) <br> - Bật **Tunnel activity log** lên CloudWatch và kiểm tra log streams <br> - Thực hành troubleshooting theo flow: **IKE → IPsec → Tunnel → Routing** (status, logs, routes, firewall rules) <br> - Đọc thêm tuỳ chọn nâng cao: StrongSwan (IKEv2), BGP (dynamic routing), Transit Gateway (optional) | 22/09/2025 | 22/09/2025 | <https://000003.awsstudygroup.com/5-vpnsitetosite/5.2-vpnsitetosite/5.2.5-modifyvpn/> <br><https://000003.awsstudygroup.com/5-vpnsitetosite/5.2-vpnsitetosite/5.2.6-alternativeconfigurations/> <br><https://000003.awsstudygroup.com/5-vpnsitetosite/5.2-vpnsitetosite/5.2.7-troubleshootingguide/> <br><http://000003.awsstudygroup.com/5-vpnsitetosite/5.2-vpnsitetosite/5.2.8-awsofficialtroubleshooting/> <br><https://000003.awsstudygroup.com/5-vpnsitetosite/5.3-vpnsitetosite-optional/> |
| 8 | - Cleanup lab để tránh phát sinh phí: terminate EC2, xoá NAT Gateway + release EIP, xoá VPC endpoints <br> - Xoá theo thứ tự: VPN connection → VPG → CGW → các VPC và thành phần liên quan <br> - Tham khảo IaC templates và cách triển khai (CloudFormation / CDK / Terraform) | 23/09/2025 | 23/09/2025 | <https://000003.awsstudygroup.com/6-cleanup/> <br><https://000003.awsstudygroup.com/7-infrastructureascode/> |


### Kết quả đạt được tuần 3:

* Thiết lập được môi trường “branch/on-prem emulator” (ASG VPN VPC + public subnet + IGW + routing) làm nền cho bài lab Site-to-Site VPN.
* Hoàn thành cấu hình Site-to-Site VPN trên AWS:
  * Tạo và attach **VPG** vào VPC ASG
  * Tạo **CGW** dựa trên public IP của EC2 Customer Gateway
  * Tạo VPN connection với **2 tunnels** để đảm bảo HA
  * Cấu hình **static routing** và bật **route propagation** cho route tables
* Cấu hình phần mềm IPsec trên Customer Gateway (OpenSwan/Libreswan/StrongSwan) và xác nhận **kết nối private IP** hai chiều qua VPN.
* Thực hành monitoring và troubleshooting với CloudWatch và quy trình kiểm tra theo thứ tự:
  * **IKE → IPsec → Tunnel → Routing**
* Dọn dẹp tài nguyên sau lab (EC2/NAT/EIP/VPN/VPC/Endpoints) để tránh chi phí phát sinh.
* Làm quen với hướng tiếp cận IaC và đọc các ví dụ template:
  * CloudFormation, AWS CDK, Terraform.
