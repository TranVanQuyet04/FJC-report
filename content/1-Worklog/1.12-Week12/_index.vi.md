---
title: "Worklog Tuần 12"
# date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 1.12. </b> "
---
<!-- {{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}} -->

### Mục tiêu tuần 12:

* Làm quen và thực hành với **AWS IAM Identity Center (AWS SSO)** để quản lý truy cập tập trung.
* Tìm hiểu mô hình quản trị nhiều tài khoản với **AWS Organizations** (tạo account, OU, switch role).
* Thực hành các cơ chế kiểm soát truy cập: **least privilege**, **time-based access control**, và **Customer Managed Policies** trong permission set.
* Làm quen với **Identity Store APIs** để tự động hóa quản lý user/group.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2 | - Đọc overview workshop, nắm bối cảnh & yêu cầu đầu vào <br> - Kiểm tra prerequisites (account, quyền admin, region khuyến nghị) | 17/11/2025 | 17/11/2025 | <https://000012.awsstudygroup.com/1-prerequisite/> |
| 3 | - Tạo các AWS account trong **AWS Organizations** (Security/Shared Services/Logging/Application) <br> - Tạo và cấu hình **Organizational Units (OU)**, di chuyển account vào OU tương ứng | 18/11/2025 | 18/11/2025 | <https://000012.awsstudygroup.com/1-prerequisite/> |
| 4 | - Thực hành mời (invite) AWS account vào Organizations (nếu có) <br> - Thực hành **Switch Role** vào member account (OrganizationAccountAccessRole) <br> - Hiểu cách áp dụng least privilege cho assume-role permissions | 19/11/2025 | 19/11/2025 | <https://000012.awsstudygroup.com/1-prerequisite/4-switch-role/> |
| 5 | - Cấu hình truy cập **AWS CLI** với IAM Identity Center <br> - So sánh 2 cách lấy credential: thủ công và `aws configure sso` (tự refresh) | 20/11/2025 | 20/11/2025 | <https://000012.awsstudygroup.com/2-aws-cli-access/> |
| 6 | - Thực hành **time-based access control**: tạo permission set + inline policy dùng điều kiện `aws:CurrentTime` <br> - Tạo group/user (vd: securityAuditors/secAuditUser), gán permission set và verify quyền truy cập | 21/11/2025 | 21/11/2025 | <https://000012.awsstudygroup.com/3-using-time-based-access-control/> |
| 7 | - Thực hành **Customer Managed Policies (CMP)** trong permission set (đồng bộ tên policy giữa các account) <br> - Làm quen **Identity Store APIs**: clone repo mẫu, chạy script Python để tạo group/user, add user vào group, list members/memberships <br> - Dọn dẹp tài nguyên: xóa CloudFormation stack (nếu có) và xóa cấu hình IAM Identity Center sau khi hoàn thành lab | 22/11/2025 | 22/11/2025 | <https://000012.awsstudygroup.com/4-using-customer-managed-policies/> <br> <https://000012.awsstudygroup.com/%CC%805-iam-identity-center-identity-store-apis/> <br> <https://000012.awsstudygroup.com/6-clean-up/#resource-cleanup> |

### Kết quả đạt được tuần 12:

* Nắm được vai trò của **AWS IAM Identity Center** trong quản lý định danh và phân quyền tập trung cho nhiều AWS account.

* Hiểu cách xây dựng nền tảng multi-account bằng **AWS Organizations**:
  * tạo member account,
  * tổ chức OU theo mục đích (Security/Logging/Shared Services/Application),
  * truy cập member account bằng **Switch Role**.

* Cấu hình và sử dụng **AWS CLI** với IAM Identity Center, hiểu lợi ích của cơ chế credential tạm thời và tự động refresh (an toàn hơn so với access key tĩnh).

* Thực hành kiểm soát truy cập theo nguyên tắc **least privilege** thông qua:
  * permission set có điều kiện thời gian (**time-based access control**),
  * tái sử dụng **Customer Managed Policies** để chuẩn hóa phân quyền giữa nhiều account.

* Làm quen cách tự động hóa quản trị user/group bằng **Identity Store APIs** (Python/Boto3): tạo group/user, quản lý membership và audit.

* Hoàn thành **cleanup** để tránh phát sinh chi phí không cần thiết sau khi kết thúc workshop.
