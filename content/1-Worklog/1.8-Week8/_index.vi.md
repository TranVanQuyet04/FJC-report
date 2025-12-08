---
title: "Worklog Tuần 8"
# date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---
<!-- {{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}} -->

### Mục tiêu tuần 8:

* Hiểu tổng quan về **Amazon CloudWatch** và vai trò của Monitoring/Observability trên AWS.
* Thực hành theo dõi **Metrics**, quản lý **Logs**, tạo **Metric Filter** (log → metric), cấu hình **Alarm** và **Dashboard**.
* Biết cách **cleanup** tài nguyên sau workshop để tránh phát sinh chi phí.
### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | ------------ | --------------- | -------------- |
| 2 | - Đọc tổng quan AWS CloudWatch Workshop <br>- Nắm kiến trúc/luồng dữ liệu: Metrics ↔ Logs ↔ Alarms ↔ Dashboards | 20/10/2025 | 20/10/2025 | <https://000008.awsstudygroup.com/1-introduction/> |
| 3 | - Thực hiện các bước chuẩn bị (Preparatory steps) theo workshop <br>- Kiểm tra các tài nguyên được tạo (EC2/Log groups/…) | 21/10/2025 | 21/10/2025 | <https://000008.awsstudygroup.com/2-preparatory-steps/> |
| 4 | - **CloudWatch Metrics:** xem và so sánh metric theo instance (CPUUtilization, EBSWriteBytes, …) <br>- Thực hành chỉnh biểu đồ: trục Y trái/phải, annotations (ngang/dọc) | 22/10/2025 | 22/10/2025 | <https://000008.awsstudygroup.com/3-cloud-watch-metric/3.1-view-metrics/> |
| 5 | - **Search expressions:** dùng `SEARCH()` để truy vấn metrics theo keyword/namespace <br>- **Math expressions:** lọc Top-N, dùng `SORT(e1, SUM, DEC, 3)` để sắp xếp/hiển thị | 23/10/2025 | 23/10/2025 | <https://000008.awsstudygroup.com/3-cloud-watch-metric/3.2-search-expression/> <br><https://000008.awsstudygroup.com/3-cloud-watch-metric/3.3-math-expression/> |
| 6 | - **Dynamic Labels:** cấu hình nhãn tự động bằng `PROP('Dim...')` để dễ đọc biểu đồ khi có nhiều metrics <br>- Ghi chú cách đặt label theo `${PROP('Dim.exe')} - ${PROP('Dim.InstanceId')} - ${PROP('MetricName')}` | 24/10/2025 | 24/10/2025 | <https://000008.awsstudygroup.com/3-cloud-watch-metric/3.4-dynamic-label/> |
| 7 | - **CloudWatch Logs:** xem log group `/ec2/linux/var/log/messages`, chỉnh retention (ví dụ 7 ngày) <br>- **Logs Insights:** tạo log từ script (logger.py), truy vấn theo ERROR/WARN, lưu query <br>- **Metric Filter:** tạo filter ERROR → metric (namespace `ec2-logs`) <br>- **Alarms:** tạo alarm khi ERROR > ngưỡng (ví dụ >10/1 phút) và gửi SNS email <br>- (Tuỳ chọn) **Dashboards:** tạo dashboard gộp metrics + alarm để quan sát tổng quan <br>- **Cleanup:** xoá CloudFormation stack & kiểm tra còn tài nguyên nào phát sinh chi phí | 25/10/2025 | 26/10/2025 | <https://000008.awsstudygroup.com/4-cloud-watch-logs/> <br><https://000008.awsstudygroup.com/4-cloud-watch-logs/4.2-logs-insights/> <br><https://000008.awsstudygroup.com/4-cloud-watch-logs/4.3-metric-filter/> <br><https://000008.awsstudygroup.com/5-cloud-watch-alarm/> <br><https://000008.awsstudygroup.com/6-cloud-watch-dashboard/> <br><https://000008.awsstudygroup.com/7-clean-up-resources/> |

### Kết quả đạt được tuần 8:

* Hiểu CloudWatch là dịch vụ **monitoring & observability** trên AWS, hỗ trợ thu thập và trực quan hóa **metrics/logs**, đồng thời tự động cảnh báo qua **alarms**.
* Thực hành xem và phân tích Metrics:
  * So sánh CPUUtilization giữa nhiều EC2 instances.
  * Quan sát tương quan giữa CPU và I/O (ví dụ EBSWriteBytes).
  * Biết cách cải thiện biểu đồ bằng trục Y trái/phải và annotations.
* Sử dụng Search/Math expressions để phân tích nâng cao:
  * Dùng `SEARCH()` để tìm metrics theo keyword/namespace.
  * Dùng `SORT()` và các phép toán đơn giản để lọc/sắp xếp dữ liệu hiển thị.
* Cấu hình Dynamic Labels giúp biểu đồ dễ đọc khi có nhiều metric/dimension.
* Thực hành CloudWatch Logs & Logs Insights:
  * Xem log group `/ec2/linux/var/log/messages`, thiết lập retention phù hợp.
  * Tạo log mẫu từ script và truy vấn theo ERROR/WARN, biết lưu query để dùng lại.
* Chuyển log thành metric bằng Metric Filter (ERROR → metric namespace `ec2-logs`) và tạo Alarm:
  * Thiết lập điều kiện cảnh báo (ví dụ ERROR > 10 trong 1 phút).
  * Tích hợp SNS email để nhận thông báo khi alarm chuyển trạng thái.
* (Tuỳ chọn) Tạo Dashboard để theo dõi tập trung metrics + alarms.
* Hoàn tất cleanup bằng cách xoá CloudFormation stack và rà soát lại các tài nguyên còn tồn đọng (metrics/logs có thể vẫn lưu theo retention).
