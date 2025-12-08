---
title: "Worklog Tuần 6"
# date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---
<!-- {{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}} -->

### Mục tiêu tuần 6:

* Hiểu và triển khai kiến trúc **High Availability + Scalability** cho ứng dụng FCJ Management bằng:
  * **EC2 Auto Scaling Group (ASG)** và **Application Load Balancer (ALB)**
* Biết cách tạo **Launch Template** từ AMI để chuẩn hoá việc nhân bản instance.
* Thực hành và so sánh các chiến lược scaling: **Manual / Scheduled / Dynamic / Predictive**.
* Biết cách chuẩn bị và đọc **CloudWatch metrics** (bao gồm custom metrics) phục vụ Predictive Scaling.
* Hoàn tất **cleanup** tài nguyên để tránh phát sinh chi phí.

### Các công việc cần triển khai trong tuần này:
### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Xem tổng quan workshop và kiến trúc mục tiêu (ALB + ASG + RDS) <br>- Xác định các thành phần cần có và luồng thao tác | 07/10/2025 | 07/10/2025 | <https://000006.awsstudygroup.com/1-introduction/> |
| 3 | - Chuẩn bị môi trường: VPC/Subnet trên nhiều AZ <br>- Cấu hình Security Group (EC2 + RDS) <br>- Launch EC2 nền (Amazon Linux 2023) | 08/10/2025 | 08/10/2025 | <https://000006.awsstudygroup.com/2-preparation/> <br><https://000006.awsstudygroup.com/2-preparation/2.1-setup-network/> <br><https://000005.awsstudygroup.com/2-prerequiste/> |
| 4 | - Tạo DB subnet group <br>- Launch Amazon RDS instance (MySQL) <br>- Kết nối từ EC2 đến RDS và khởi tạo database + tables + dữ liệu mẫu | 09/10/2025 | 09/10/2025 | <https://000006.awsstudygroup.com/2-preparation/2.3-launch-db-instance/> <br><https://000006.awsstudygroup.com/2-preparation/2.4-add-data-to-db/> |
| 5 | - Deploy FCJ Management web server trên EC2 (Node.js + PM2) <br>- Cấu hình `.env` để kết nối DB <br>- Xác minh ứng dụng chạy đúng trên port 5000 | 10/10/2025 | 10/10/2025 | <https://000006.awsstudygroup.com/2-preparation/2.5-deploy-web-server/> |
| 6 | - Tạo AMI từ EC2 đã cấu hình và tạo Launch Template <br>- Tạo Target Group (HTTP:5000) và ALB (internet-facing) <br>- Tạo Auto Scaling Group và gắn Target Group của ALB <br>- Chuẩn bị/ upload custom metrics cho Predictive Scaling trên CloudWatch | 11/10/2025 | 11/10/2025 | <https://000006.awsstudygroup.com/3-create-launch-template/> <br><https://000006.awsstudygroup.com/4-setup-load-balancer/> <br><https://000006.awsstudygroup.com/6-create-auto-scaling-group/> <br><https://000006.awsstudygroup.com/2-preparation/2.6-prepare-metrics-for-predictive-scaling/> |
| 7 | - Test các giải pháp scaling (manual / scheduled / dynamic / predictive) <br>- Quan sát hành vi scale-out / scale-in và ghi nhận kết quả <br>- Cleanup tài nguyên (ASG, ALB, TG, LT, AMI, EC2, RDS, subnet group, snapshots,...) | 12/10/2025 | 12/10/2025 | <https://000006.awsstudygroup.com/7-test-solutions/7.1-test-manual-scaling-solution/> <br><https://000006.awsstudygroup.com/7-test-solutions/7.2-test-scheduled-scaling-solution/> <br><https://000006.awsstudygroup.com/7-test-solutions/7.3-test-dynamic-scaling-solution/> <br><https://000006.awsstudygroup.com/7-test-solutions/7.4-test-predictive-scaling-solution/> <br><https://000006.awsstudygroup.com/8-cleanup-resources/> |

### Kết quả đạt được tuần 6:

* Nắm được kiến trúc triển khai ứng dụng theo hướng **co giãn và chịu lỗi**:
  * ALB phân phối request tới các instance trong Target Group.
  * ASG tự động tăng/giảm số lượng instance theo nhu cầu.

* Chuẩn hoá triển khai bằng AMI và Launch Template:
  * Tạo AMI từ instance đã cấu hình sẵn app.
  * Tạo Launch Template để tái sử dụng cấu hình (AMI, instance type, key pair, SG…).

* Hoàn thành cấu hình Load Balancer:
  * Tạo Target Group port **5000** và cấu hình health check.
  * Tạo ALB internet-facing, trỏ listener về Target Group và test truy cập bằng DNS.

* Hoàn thành Auto Scaling Group:
  * ASG chạy đa AZ, gắn với Target Group của ALB.
  * Bật ELB health check và CloudWatch group metrics.

* Thực hành các chiến lược scaling và rút ra điểm khác nhau:
  * **Manual scaling:** can thiệp thủ công, phù hợp lab/demo nhưng không tối ưu vận hành.
  * **Scheduled scaling:** phù hợp workload theo lịch (giờ cao điểm cố định).
  * **Dynamic scaling (target tracking):** scale theo metric thực tế (ví dụ request/target), phản ứng tốt cho traffic khó đoán nhưng có độ trễ do cập nhật metric.
  * **Predictive scaling:** dùng dữ liệu lịch sử + forecast để “đón đầu” peak, có thể kết hợp dynamic để tăng độ linh hoạt.

* Chuẩn bị và đọc metrics cho Predictive Scaling:
  * Upload custom metrics lên CloudWatch.
  * Biết cách đọc biểu đồ forecast và quy đổi múi giờ **UTC → UTC+7** khi phân tích.

* Dọn tài nguyên tốt để tránh phát sinh chi phí:
  * Xoá ASG → ALB → Target Group → Launch Template → Deregister AMI (+ xoá snapshots nếu cần) → terminate EC2 → xoá RDS/Subnet group và các tài nguyên mạng liên quan.
