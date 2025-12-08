---
title: "Worklog Tuần 4"
# date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---
<!-- {{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}} -->

### Mục tiêu tuần 4:

* Hoàn thành workshop **Amazon EC2 (000004)** theo luồng end-to-end: **chuẩn bị network → launch instance → EC2 basics → deploy app → governance → cleanup**.
* Chuẩn bị hạ tầng cần thiết cho lab:
  * Tạo **VPC** cho workload **Linux** và **Windows**.
  * Tạo **Security Group** theo nguyên tắc **least privilege** cho SSH/RDP/HTTP/HTTPS và port ứng dụng.
* Thực hành các thao tác EC2 cốt lõi:
  * Thay đổi **instance type**
  * Tạo **EBS snapshot**
  * Tạo **custom AMI** và launch instance từ AMI
  * Ôn các phương pháp **khôi phục truy cập** cơ bản (Windows/Linux)
* Triển khai ứng dụng mẫu **AWS FCJ User Management (Node.js CRUD)**:
  * Trên **Linux** (LAMP + Node.js)
  * Trên **Windows** (XAMPP + Node.js)
* Thực hành **Cost & Usage Governance với IAM** (giới hạn region/service/resource) và **dọn dẹp tài nguyên** để tránh phát sinh chi phí.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2 | - Đọc tổng quan workshop & các module **Amazon EC2 (000004)** | 24/09/2025 | 24/09/2025 | <http://000004.awsstudygroup.com/1-introduce/> |
| 3 | - Chuẩn bị: tạo **Linux VPC** + **Windows VPC** <br>- Tạo **Linux-SG** + **Windows-SG** (các inbound port cần thiết cho lab) | 25/09/2025 | 25/09/2025 | <https://000004.awsstudygroup.com/2-prerequiste/> <br> <https://000004.awsstudygroup.com/2-prerequiste/2.1-createvpclinuxinstance/> <br> <https://000004.awsstudygroup.com/2-prerequiste/2.2-createvpcwindowsinstance/> <br> <https://000004.awsstudygroup.com/2-prerequiste/2.3-createsecuritygrouplinux/> <br> <https://000004.awsstudygroup.com/2-prerequiste/2.4-createsecuritygroupwindows/> |
| 4 | - Launch **Windows Server 2022** instance <br>- Kết nối instance qua **RDP** và xác thực truy cập | 26/09/2025 | 26/09/2025 | <https://000004.awsstudygroup.com/3-launchwindowsinstance/> <br> <https://000004.awsstudygroup.com/3-launchwindowsinstance/3.1-createwindowssintance/> <br> <https://000004.awsstudygroup.com/3-launchwindowsinstance/3.2-connectwindowsinstance/> |
| 5 | - Launch **Amazon Linux** instance <br>- Kết nối qua **SSH**, kiểm tra SG rules và networking | 27/09/2025 | 27/09/2025 | <https://000004.awsstudygroup.com/4-launchlinuxinstance/> <br> <https://000004.awsstudygroup.com/4-launchlinuxinstance/4.1-createlinuxinstance/> <br> <https://000004.awsstudygroup.com/4-launchlinuxinstance/4.2-connectlinuxinstance/> |
| 6 | - Thực hành EC2 Basic: <br>&emsp; + Đổi instance type <br>&emsp; + Tạo snapshot <br>&emsp; + Tạo custom AMI & launch từ AMI <br>&emsp; + Ôn khôi phục truy cập (Windows/Linux) <br>- Deploy app trên **Linux** (LAMP + phpMyAdmin + Node.js CRUD) <br>- Deploy app trên **Windows** (XAMPP + Node.js) <br>- Thực hành IAM governance và **cleanup** (terminate instances, xóa AMI/snapshot/SG/VPC/policies) | 28/09/2025 | 30/09/2025 | <https://000004.awsstudygroup.com/5-amazonec2basic/> <br> <https://000004.awsstudygroup.com/5-amazonec2basic/5.1-changeconfigureec2/> <br> <https://000004.awsstudygroup.com/5-amazonec2basic/5.2-createec2snapshot/> <br> <https://000004.awsstudygroup.com/5-amazonec2basic/5.3-createcustomami/> <br> <https://000004.awsstudygroup.com/5-amazonec2basic/5.4-launchec2ami/> <br> <https://000004.awsstudygroup.com/5-amazonec2basic/5.5-keypair-ssm-windows/> <br> <https://000004.awsstudygroup.com/5-amazonec2basic/5.6-keypair-user-data-linux/> <br> <https://000004.awsstudygroup.com/6-awsfcjmanagement-linux/> <br> <https://000004.awsstudygroup.com/6-awsfcjmanagement-linux/6.1-lampserveronec2linux/> <br> <https://000004.awsstudygroup.com/6-awsfcjmanagement-linux/6.2-setupnodejsonec2linux/> <br> <https://000004.awsstudygroup.com/6-awsfcjmanagement-linux/6.3-awsfcjmanagement/> <br> <https://000004.awsstudygroup.com/7-awsfcjmanagement-windows/> <br> <https://000004.awsstudygroup.com/7-awsfcjmanagement-windows/7.1-xampponwindows/> <br> <https://000004.awsstudygroup.com/7-awsfcjmanagement-windows/7.3-awsfcjmanagement/> <br> <https://000004.awsstudygroup.com/8-costusagegovernance/> <br> <https://000004.awsstudygroup.com/8-costusagegovernance/8.1-iamretrictregion/> <br> <https://000004.awsstudygroup.com/8-costusagegovernance/8.2-iamretrictec2family/> <br> <https://000004.awsstudygroup.com/8-costusagegovernance/8.3-iamretrictec2size/> <br> <https://000004.awsstudygroup.com/8-costusagegovernance/8.4-iamretrictecebs/> <br> <https://000004.awsstudygroup.com/8-costusagegovernance/8.5-iamretricteip/> <br> <https://000004.awsstudygroup.com/8-costusagegovernance/8.6-iamretrictetime/> <br> <https://000004.awsstudygroup.com/9-cleanup/> |

### Kết quả đạt được tuần 4:

* Hoàn thành workflow workshop **Amazon EC2 (000004)**: **Prerequisite → Launch Instances → EC2 Basic → Deploy App → Governance → Cleanup**.
* Thiết lập được môi trường chạy lab:
  * VPC + subnet/public IP settings cho Linux/Windows
  * Security Group đủ các port cần thiết (SSH/RDP/HTTP/HTTPS/ICMP + port ứng dụng)
* Thực hành các kỹ năng EC2 cốt lõi:
  * Đổi instance type
  * Tạo EBS snapshot
  * Tạo custom AMI và launch instance từ AMI
  * Nắm các hướng khôi phục truy cập (Windows/Linux) ở mức cơ bản
* Deploy thành công **AWS FCJ User Management**:
  * Linux: LAMP/MariaDB/phpMyAdmin + Node.js app và kiểm thử CRUD
  * Windows: XAMPP + Node.js và kiểm thử chức năng
* Thực hành IAM governance để kiểm soát chi phí/rủi ro: giới hạn region và ràng buộc EC2 (family/size), kèm EBS/EIP/time-based control.
* Dọn dẹp đầy đủ tài nguyên (instances/AMI/snapshots/SG/VPC/IAM policies…) để tránh phát sinh chi phí.
