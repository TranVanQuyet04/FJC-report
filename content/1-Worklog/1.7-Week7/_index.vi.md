---
title: "Worklog Tuần 7"
# date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---
<!-- {{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}} -->

### Mục tiêu tuần 7:

* Hiểu về **Cost Management/Cost Governance** trên AWS và vai trò của **AWS Budgets** trong việc theo dõi chi phí & mức sử dụng.
* Thực hành tạo các loại ngân sách (Budget) phổ biến và cấu hình cảnh báo (alerts/notifications).
* Biết cách **dọn dẹp (cleanup)** budgets sau khi lab để tránh gửi email cảnh báo không cần thiết.

### Các công việc cần triển khai trong tuần này:
### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Đọc tổng quan workshop AWS Budgets <br>- Ghi chú khái niệm: cost budget/usage budget/RI budget/savings plans budget <br>- Ghi chú best practices (nhiều ngưỡng cảnh báo, quyền tối thiểu, độ trễ dữ liệu billing) | 13/10/2025 | 13/10/2025 | <https://000007.awsstudygroup.com/> |
| 3 | - **Thực hành:** Tạo Budget theo **Template** (Monthly cost budget) <br>- Kiểm tra các ngưỡng cảnh báo mặc định (actual + forecast) | 14/10/2025 | 14/10/2025 | <https://000007.awsstudygroup.com/0-createtemplate/> |
| 4 | - **Thực hành:** Tạo **Cost Budget** (Customize/Advanced) <br>- Cấu hình nhiều ngưỡng cảnh báo (ví dụ: 50% / 80% / 90% / 100%) <br>- Kiểm tra Budget overview & budget history | 15/10/2025 | 15/10/2025 | <https://000007.awsstudygroup.com/1-cost-budgets/> |
| 5 | - **Thực hành:** Tạo **Usage Budget** (ví dụ: EC2 Running Hours) <br>- Thiết lập cảnh báo actual/forecasted <br>- Ghi chú độ trễ cập nhật dữ liệu (billing/usage không realtime) | 16/10/2025 | 16/10/2025 | <https://000007.awsstudygroup.com/2-usage-budget/> |
| 6 | - **Thực hành:** Tạo **RI Budget** (coverage/utilization) <br>- **Thực hành:** Tạo **Savings Plans Budget** (coverage/utilization) <br>- Ghi chú: Lab mô phỏng, không cần mua RI/Savings Plans thật | 17/10/2025 | 17/10/2025 | <https://000007.awsstudygroup.com/3-reservation-budget/> <br><https://000007.awsstudygroup.com/4-saving-plans-budget/> |
| 7 | - Rà soát toàn bộ budgets đã tạo (tên, scope, alert, email nhận) <br>- **Cleanup:** Xóa budgets của lab để tránh gửi cảnh báo về sau <br>- Xác minh danh sách Budgets đã sạch | 18/10/2025 | 18/10/2025 | <https://000007.awsstudygroup.com/5-clean-up/> |

### Kết quả đạt được tuần 7:

* Nắm được AWS Budgets là gì và cách Budgets hỗ trợ **giám sát chi phí & mức sử dụng** theo ngưỡng (threshold) và theo dự báo (forecast).
* Phân biệt và hiểu mục đích các loại budget phổ biến:
  * **Cost Budget**: theo dõi chi phí ($)
  * **Usage Budget**: theo dõi mức sử dụng dịch vụ (ví dụ EC2 hours)
  * **RI Budget**: theo dõi coverage/utilization của Reserved Instances
  * **Savings Plans Budget**: theo dõi coverage/utilization của Savings Plans
* Thực hành tạo budget theo 2 hướng:
  * **Template (simplified)**: tạo nhanh theo mẫu có sẵn
  * **Customize (advanced)**: tùy chỉnh phạm vi, chu kỳ, ngưỡng cảnh báo và người nhận
* Cấu hình cảnh báo và ghi chú các điểm quan trọng:
  * Dữ liệu billing/usage cập nhật theo chu kỳ nên cảnh báo có thể **trễ** so với thực tế.
  * Forecast alerts có thể kích hoạt nhiều lần nếu dự báo thay đổi.
* Hoàn tất **cleanup** budgets của lab để tránh spam email và giữ tài khoản gọn gàng.
