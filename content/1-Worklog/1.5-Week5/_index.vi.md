---
title: "Worklog Tuần 5"
# date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---
<!-- {{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}} -->

### Mục tiêu tuần 5:

* Hiểu các khái niệm cốt lõi của **Amazon RDS** (CSDL quan hệ dạng managed, engine hỗ trợ, storage, HA/DR, bảo mật).
* Xây dựng nền tảng mạng cần thiết cho RDS:
  * Tạo **VPC**, các subnet trên nhiều AZ, và **DB Subnet Group**.
  * Tạo **Security Group** tách biệt cho EC2 (app) và RDS (DB) theo nguyên tắc least privilege.
* Khởi tạo tài nguyên và kiểm tra kết nối:
  * Launch **EC2 (Amazon Linux 2023)** làm máy chủ ứng dụng.
  * Tạo **RDS DB instance** và lấy endpoint/port để cấu hình kết nối ứng dụng.
* Triển khai ứng dụng mẫu **Node.js** và kết nối đến **RDS**.
* Thực hành **backup/restore** bằng snapshot của RDS.
* Thực hiện **cleanup** đầy đủ để tránh phát sinh chi phí.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2 | - Đọc phần giới thiệu workshop & tổng quan RDS (tính năng, engine, backup, bảo mật) | 10/01/2025 | 10/01/2025 | <https://000005.awsstudygroup.com/1-introduce/> |
| 3 | - Hoàn thành prerequisite: <br>&emsp; + Tạo VPC (subnet trên tối thiểu 2 AZ) <br>&emsp; + Tạo Security Group cho EC2 (HTTP/HTTPS/SSH/app port) <br>&emsp; + Tạo Security Group cho RDS (chỉ mở DB port từ EC2-SG) <br>&emsp; + Tạo DB Subnet Group | 10/02/2025 | 10/02/2025 | <https://000005.awsstudygroup.com/2-prerequiste/> <br> <https://000005.awsstudygroup.com/2-prerequiste/1-create-vpc/> <br> <https://000005.awsstudygroup.com/2-prerequiste/2-create-ec2-sg/> <br> <https://000005.awsstudygroup.com/2-prerequiste/3-create-db-sg/> <br> <https://000005.awsstudygroup.com/2-prerequiste/4-create-db-subnetgroup/> |
| 4 | - Tạo EC2 instance (Amazon Linux 2023) <br>- Kết nối SSH vào EC2 và chuẩn bị môi trường chạy (Git/dependencies cho Node.js) | 10/03/2025 | 10/03/2025 | <https://000005.awsstudygroup.com/3-create-ec2/> |
| 5 | - Tạo Amazon RDS database instance (lấy Endpoint/Port/Username) <br>- Xác minh luồng kết nối theo security group (EC2 → RDS) | 10/04/2025 | 10/04/2025 | <https://000005.awsstudygroup.com/4-create-rds/> |
| 6 | - Deploy ứng dụng: clone repo, cài packages, cấu hình `.env` trỏ đến RDS endpoint <br>- Tạo database/table và insert dữ liệu test <br>- Xác minh ứng dụng chạy và kết nối RDS thành công <br>- Thực hành backup & restore bằng DB snapshot <br>- Cleanup tài nguyên (RDS/EC2/VPC/SG/Subnet group/snapshots/EIP/NAT nếu có tạo) | 10/05/2025 | 10/06/2025 | <https://000005.awsstudygroup.com/5-deploy-app/> <br> <https://000005.awsstudygroup.com/6-backup/> <br> <https://000005.awsstudygroup.com/7-cleanup/> |

### Kết quả đạt được tuần 5:

* Nắm vững kiến thức nền tảng về **Amazon RDS**:
  * Dịch vụ CSDL managed cho workload OLTP, hỗ trợ các engine như Aurora, MySQL, MariaDB, PostgreSQL, Oracle và SQL Server.
  * Các khả năng chính: automated backups, maintenance windows, scaling options, encryption và cô lập mạng qua VPC.

* Hoàn thành cấu hình prerequisite về mạng và bảo mật:
  * Tạo **VPC** riêng và đảm bảo subnet trải trên tối thiểu **2 Availability Zones** để đáp ứng yêu cầu Multi-AZ.
  * Tạo tách biệt **Security Groups**:
    * **EC2 SG** phục vụ truy cập web/app và quản trị (giới hạn nguồn SSH khi phù hợp).
    * **RDS SG** chỉ cho phép truy cập DB port **từ EC2 SG** (không mở public IP ranges).

* Khởi tạo compute + database thành công:
  * Launch **Amazon Linux 2023 EC2** và chuẩn bị môi trường (Git / Node.js).
  * Tạo **RDS DB instance** và xác nhận thông tin endpoint/port để ứng dụng kết nối.

* Deploy và kiểm thử ứng dụng với RDS:
  * Clone repo, cài dependencies cho Node.js, cấu hình biến kết nối trong `.env`.
  * Tạo schema (DB + bảng `user`) và insert dữ liệu mẫu.
  * Xác minh ứng dụng hoạt động end-to-end (CRUD) và dữ liệu được lưu trên **RDS**.

* Thực hành bảo vệ và khôi phục dữ liệu:
  * Theo dõi backup trên RDS và thực hiện **snapshot restore**, lưu ý restore tạo **DB instance endpoint mới** nên có thể cần cập nhật cấu hình ứng dụng.

* Cleanup đầy đủ để kiểm soát chi phí:
  * Xóa DB instance, snapshots, subnet group (nếu có tạo) và các tài nguyên mạng liên quan; terminate EC2 và gỡ các thành phần hỗ trợ để tránh phát sinh phí.
