---
title: "Worklog Tuần 2"
# date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---
<!-- {{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}} -->


### Mục tiêu tuần 2:

* Tìm hiểu và thực hành **AWS Identity and Access Management (IAM)** theo hướng kiểm soát truy cập an toàn.
* Hiểu các thành phần cốt lõi của IAM: **User / Group / Policy / Role** và nguyên tắc **Least Privilege**.
* Thiết lập mô hình quản trị khuyến nghị:
  * Tạo **Admin Group + Admin User** để quản trị thay cho root user.
  * Tạo **AdminRole** và **OperatorUser**, thực hành cơ chế **AssumeRole** và **Switch Role**.
* Làm quen cách cấu hình **Trust policy** (ai được assume role) và **Permission policy** (role làm được gì).
* Thực hiện **clean up** tài nguyên IAM sau khi lab để đảm bảo bảo mật và tránh rủi ro.


### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Đọc tổng quan IAM (khái niệm user/group/policy/role) <br>- Ghi chú best practices (MFA, root user, least privilege, CloudTrail) | 12/09/2025 | 12/09/2025 | <https://000002.awsstudygroup.com/1-introduction/> <br> <https://000002.awsstudygroup.com/1-introduction/1.1-group-user/> <br> <https://000002.awsstudygroup.com/1-introduction/1.2-iam-policy/> |
| 3 | - Thực hành tạo **IAM Admin Group** và gán **AdministratorAccess** <br>- Tạo **AdminUser** và thêm vào Admin Group | 13/09/2025 | 13/09/2025 | <https://000002.awsstudygroup.com/2-create-admin-user-and-group/2.1-create-admin-group/> |
| 4 | - Đăng nhập AWS bằng **AdminUser** qua console sign-in URL <br>- Kiểm tra quyền và điều hướng dịch vụ IAM | 14/09/2025 | 14/09/2025 | <https://000002.awsstudygroup.com/2-create-admin-user-and-group/2.1-create-admin-group/> |
| 5 | - Thực hành tạo **AdminRole** (attach AdministratorAccess) <br>- Tạo **OperatorUser** (không gán quyền trực tiếp) | 15/09/2025 | 15/09/2025 | <https://000002.awsstudygroup.com/3-aws-role/> |
| 6 | - Cấu hình cho OperatorUser được **sts:AssumeRole** vào AdminRole (inline policy) <br>- Đăng nhập OperatorUser và **Switch Role** sang AdminRole <br>- **Clean up**: xóa user/group/role/policy lab | 16/09/2025 | 16/09/2025 | <https://000002.awsstudygroup.com/4-switch-roles/> <br> <https://000002.awsstudygroup.com/4-switch-roles/4.2-login-operatoruser/> <br> <https://000002.awsstudygroup.com/4-switch-roles/4.3-switchrole/> <br> <https://000002.awsstudygroup.com/5-cleanup/> |



### Kết quả đạt được tuần 2:

* Nắm được kiến thức nền tảng về **AWS IAM** và vai trò của IAM trong kiểm soát truy cập tài nguyên AWS:
  * IAM User, IAM Group, IAM Policy, IAM Role
  * Khác nhau giữa **Permission policy** và **Trust policy**
  * Hiểu nguyên tắc **Least Privilege** và lý do không nên dùng root user cho tác vụ hằng ngày

* Thiết lập thành công cấu trúc quản trị cơ bản theo best practices:
  * Tạo **Admin Group** và gán **AdministratorAccess**
  * Tạo **AdminUser** và thêm vào Admin Group để quản trị AWS thông qua IAM

* Thực hành mô hình phân quyền nâng cao dựa trên **IAM Role**:
  * Tạo **AdminRole** và attach **AdministratorAccess**
  * Tạo **OperatorUser** (không gán quyền trực tiếp ban đầu)

* Cấu hình quyền cho OperatorUser thực hiện **AssumeRole**:
  * Gắn inline policy cho OperatorUser với quyền `sts:AssumeRole` vào `AdminRole`
  * Đăng nhập bằng OperatorUser và thực hiện **Switch Role** sang AdminRole để nhận quyền quản trị tạm thời

* Hoàn thành bước **clean up** sau lab:
  * Xóa các IAM resources đã tạo (users/groups/roles/policies) để tránh rủi ro bảo mật và đảm bảo hệ thống gọn gàng
