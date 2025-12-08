---
title: "Worklog Tuần 10"
# date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.10. </b> "
---
<!-- {{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}} -->

### Mục tiêu tuần 10:

* Nắm được kiến trúc **Hybrid DNS** giữa DNS on-premises và AWS bằng **Route 53 Resolver**.
* Thực hành triển khai hạ tầng cần thiết bằng **CloudFormation / Quick Start**.
* Cấu hình **Resolver Endpoints + Resolver Rules** và kiểm thử phân giải DNS.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2 | - Đọc tổng quan workshop và các khái niệm chính: Route 53, Route 53 Resolver <br> - Hiểu Inbound/Outbound endpoints và Resolver rules | 03/11/2025 | 03/11/2025 | <https://000010.awsstudygroup.com/> |
| 3 | - Tạo EC2 key pair để truy cập an toàn (phục vụ giải mã mật khẩu Windows) | 04/11/2025 | 04/11/2025 | <https://000010.awsstudygroup.com/2-prerequiste/2.1-createkeypair/> |
| 4 | - Triển khai hạ tầng mạng bằng **CloudFormation (AWS Quick Start RDGW)** <br> - Kiểm tra VPC/Subnets đã tạo và stack outputs | 05/11/2025 | 05/11/2025 | <https://000010.awsstudygroup.com/2-prerequiste/2.2-launchcloudformation/> |
| 5 | - Cấu hình Security Group (giới hạn port, chỉ cho phép truy cập cần thiết từ IP tin cậy) | 06/11/2025 | 06/11/2025 | <https://000010.awsstudygroup.com/2-prerequiste/2.3-security/> |
| 6 | - Kết nối RDGW bằng RDP <br> - Dùng PEM để decrypt mật khẩu Administrator và đăng nhập Windows | 07/11/2025 | 07/11/2025 | <https://000010.awsstudygroup.com/3-connecttordgw/> |
| 7 | - Triển khai **AWS Managed Microsoft AD** (mô phỏng DNS on-premises) trong private subnets; ghi lại DNS IP của Directory Service <br> - Tạo Route 53 Resolver **Outbound Endpoint** <br> - Tạo **Resolver Rule** để forward `onprem.example.com` tới DNS IP của AD <br> - (Nếu có trong lab) tạo **Inbound Endpoint** để on-prem → AWS resolution <br> - Kiểm thử bằng `nslookup` / `Resolve-DnsName` trên RDGW <br> - Cleanup: xóa endpoints, disassociate & xóa rules, xóa Directory, xóa CloudFormation stack | 08/11/2025 | 08/11/2025 | <https://000010.awsstudygroup.com/4-setupad/> <br> <https://000010.awsstudygroup.com/5-setuphyriddns/> <br> <https://000010.awsstudygroup.com/6-cleanup/> |

### Kết quả đạt được tuần 10:

* Hiểu được bài toán **Hybrid DNS** và lý do cần tích hợp hệ thống DNS on-premises với AWS (đảm bảo đồng bộ domain nội bộ và tài nguyên trên cloud).

* Nắm rõ 3 thành phần chính của **Route 53 Resolver** trong mô hình hybrid:
  * **Outbound Endpoint**: forward truy vấn từ VPC ra DNS “on-prem”
  * **Inbound Endpoint**: nhận truy vấn từ “on-prem” vào AWS/VPC
  * **Resolver Rules**: định tuyến truy vấn theo domain (Forward / System)

* Triển khai thành công hạ tầng nền bằng **AWS CloudFormation / Quick Start**, sẵn sàng cho việc cấu hình DNS hybrid.

* Tạo và cấu hình **AWS Managed Microsoft AD** (giả lập DNS on-prem), ghi nhận DNS IP để dùng làm target trong Resolver Rule.

* Cấu hình thành công luồng forward DNS cho `onprem.example.com` thông qua:
  * Route 53 Resolver **Outbound Endpoint**
  * **Forward rule** trỏ đến DNS IP của Directory Service

* Kiểm thử phân giải DNS trên máy Windows (RDGW) bằng:
  * `nslookup onprem.example.com`
  * `Resolve-DnsName onprem.example.com`

* Hoàn tất **cleanup** toàn bộ tài nguyên lab để tránh phát sinh chi phí (Route 53 Resolver resources, Directory Service, CloudFormation stack).
