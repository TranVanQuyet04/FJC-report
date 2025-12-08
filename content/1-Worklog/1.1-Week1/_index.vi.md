---
title: "Worklog Tuần 1"
# date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---
<!-- {{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}} -->

### Mục tiêu tuần 1:

* Kết nối, làm quen với các thành viên trong First Cloud Journey (FCJ).
* Nắm kiến thức nền tảng về AWS: khái niệm, nhóm dịch vụ cơ bản.
* Làm quen với AWS Management Console và hiểu cách thao tác quản trị từ giao diện web.
* Cài đặt, cấu hình và thực hành các thao tác cơ bản với AWS CLI.
* Bắt đầu tìm hiểu và thực hành EC2 (tạo instance, SSH, EBS, Elastic IP).

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Làm quen với các thành viên FCJ <br>- Đọc và lưu ý các nội quy, quy định tại đơn vị thực tập | 05/09/2025 | 05/09/2025 |  |
| 3 | - Tìm hiểu AWS và các loại dịch vụ <br>&emsp; + Compute <br>&emsp; + Storage <br>&emsp; + Networking <br>&emsp; + Database | 08/09/2025 | 08/09/2025 | <https://000001.awsstudygroup.com/> |
| 4 | - Tạo AWS Free Tier account (theo workshop) <br>- Thiết lập MFA cho root user (Virtual MFA / Security key / Hardware MFA) <br>- Tạo Admin User & Admin Group để quản trị thay root user | 09/09/2025 | 09/09/2025 | <https://000001.awsstudygroup.com/1-create-new-aws-account/> <br> <https://000001.awsstudygroup.com/1-create-new-aws-account/1.1-find-account-id/> <br> <https://000001.awsstudygroup.com/1-create-new-aws-account/1.2-update-account/> <br> <https://000001.awsstudygroup.com/2-mfa-setup-for-aws-user-root/1-virtual-mfa-device/> <br> <https://000001.awsstudygroup.com/2-mfa-setup-for-aws-user-root/2-u2f-security-key/> <br> <https://000001.awsstudygroup.com/2-mfa-setup-for-aws-user-root/3-other-hardware-mfa-device/> <br> <https://000001.awsstudygroup.com/3-create-admin-user-and-group/> |
| 5 | - Xác thực “new account” và chuẩn bị kênh hỗ trợ (Account Authentication/Support) <br>- Khám phá & cấu hình AWS Management Console (default region, search, favorites, widgets) | 10/09/2025 | 10/09/2025 | <https://000001.awsstudygroup.com/4-verify-new-account/> <br> <https://000001.awsstudygroup.com/5-explore-and-configure-the-aws-management-console/> <br> <https://000001.awsstudygroup.com/5-explore-and-configure-the-aws-management-console/5.1-config-default-region/> <br> <https://000001.awsstudygroup.com/5-explore-and-configure-the-aws-management-console/5.2-search-with-the-aws-management-console/> <br> <https://000001.awsstudygroup.com/5-explore-and-configure-the-aws-management-console/5.3-add-and-remove-favorites/> <br> <https://000001.awsstudygroup.com/5-explore-and-configure-the-aws-management-console/5.4create-and-use-dashboard-widgets/> |
| 6 | - Tạo Support case và làm quen Case Management (Billing/Limit increase/Technical) <br>- Ôn lại thao tác console (search) và dashboard widgets | 11/09/2025 | 11/09/2025 | <https://000001.awsstudygroup.com/6-support-cases/> <br> <https://000001.awsstudygroup.com/5-explore-and-configure-the-aws-management-console/5.2-search-with-the-aws-management-console/> <br> <https://000001.awsstudygroup.com/5-explore-and-configure-the-aws-management-console/5.4create-and-use-dashboard-widgets/> |

### Kết quả đạt được tuần 1:

* Hiểu AWS là gì và nắm được các nhóm dịch vụ cơ bản:
  * Compute  
  * Storage  
  * Networking  
  * Database  

* Tạo và cấu hình AWS Free Tier account thành công theo hướng best practices:
  * Thiết lập MFA cho root user
  * Tạo Admin User & Admin Group để tránh dùng root user hằng ngày

* Làm quen với AWS Management Console:
  * Biết cách cấu hình default region, tìm kiếm dịch vụ, quản lý favorites, và tùy biến dashboard widgets.

* Nắm được quy trình hỗ trợ & vận hành tài khoản:
  * Hiểu cách verify tài khoản mới và cách tạo/quản lý support cases trên AWS Support Center.

* Có khả năng thao tác và học tiếp theo lộ trình workshop:
  * Biết “đi đường” theo các lab của workshop (account → MFA → admin user/group → console → support).
