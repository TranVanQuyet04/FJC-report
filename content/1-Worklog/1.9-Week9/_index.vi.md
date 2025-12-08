---
title: "Worklog Tuần 9"
# date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---
<!-- {{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn (kể cả warning này).
{{% /notice %}} -->

### Mục tiêu tuần 9:

* Tìm hiểu tổng quan **AWS Support** và các gói hỗ trợ.
* Biết cách truy cập **Support Center**, tạo và quản lý **support case**.
* Hiểu cách chọn **Severity** phù hợp theo mức độ ảnh hưởng của sự cố.
### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2 | - Đọc tổng quan AWS Support <br>- Nắm khi nào cần dùng AWS Support | 27/10/2025 | 27/10/2025 | <https://000009.awsstudygroup.com/> |
| 3 | - Tìm hiểu các gói AWS Support: **Basic / Developer / Business / Enterprise** <br>- So sánh quyền lợi theo từng gói | 28/10/2025 | 28/10/2025 | <https://000009.awsstudygroup.com/1-support-plans/> |
| 4 | - Tìm hiểu các loại support request (case): <br>&emsp; + Account & Billing <br>&emsp; + Service limit increase <br>&emsp; + Technical support | 29/10/2025 | 29/10/2025 | <https://000009.awsstudygroup.com/2-access-support/2.1-support-types/> |
| 5 | - Tìm hiểu cách **đổi support plan** (ví dụ: Basic → Developer) | 30/10/2025 | 30/10/2025 | <https://000009.awsstudygroup.com/2-access-support/2.2-change-support-package/> |
| 6 | - **Thực hành/giả lập:** Tạo support case trên AWS Support Center <br>- Điền: Type, Category, Subject, Description, Attachments, Contact method | 31/10/2025 | 31/10/2025 | <https://000009.awsstudygroup.com/3-manage-cases/3.1-create-request/> |
| 7 | - Tìm hiểu cách chọn **Severity** và response time theo từng gói <br>- Ghi chú cách chọn severity phù hợp theo mức độ ảnh hưởng | 01/11/2025 | 01/11/2025 | <https://000009.awsstudygroup.com/3-manage-cases/3.2-select-severity/> |

### Kết quả đạt được tuần 9:

* Hiểu được **AWS Support** là gì và khi nào cần dùng Support Center.
* Nắm được các gói AWS Support (Basic, Developer, Business, Enterprise) và điểm khác nhau cơ bản:
  * Basic: chủ yếu hỗ trợ account/billing và request tăng service limit.
  * Các gói cao hơn: mở rộng phạm vi tư vấn kỹ thuật, best practices, công cụ (ví dụ Trusted Advisor ở Business trở lên), và mức độ ưu tiên xử lý.
* Phân biệt được 3 loại **Support Requests**:
  * **Account and Billing support** (phổ biến, ai cũng dùng được)
  * **Service limit increase**
  * **Technical support** (phụ thuộc gói; Basic không tạo technical case)
* Biết quy trình **đổi support plan** (ví dụ chuyển sang Developer khi cần kỹ thuật nhiều hơn).
* Biết cách tạo và quản lý một **support case** trong AWS Support:
  * Chọn đúng Type/Category
  * Viết Subject/Description rõ ràng, đính kèm ảnh khi cần
  * Chọn phương thức liên hệ (chat/email/phone tùy gói)
* Hiểu quy tắc chọn **Severity** phù hợp (General Guidance → System Impaired → Production Impaired → Production Down, …) và lưu ý response time của gói Developer chỉ tính trong giờ hành chính.
