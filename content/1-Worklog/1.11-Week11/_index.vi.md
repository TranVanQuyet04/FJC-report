---
title: "Worklog Tuần 11"
# date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---
<!-- {{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}} -->

### Mục tiêu tuần 11:

* Học và thực hành sử dụng **AWS CLI v2** để quản lý tài nguyên AWS hiệu quả hơn.
* Hiểu các khái niệm khi dùng AWS CLI: **credentials, profiles, region, output format**, và troubleshooting cơ bản.
* Thực hành AWS CLI với các dịch vụ cơ bản: **S3, IAM, VPC, EC2** và thực hiện **cleanup** đúng cách.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2 | - Đọc tổng quan workshop “Getting Started with the AWS CLI” <br> - Nắm khái niệm AWS CLI, môi trường hỗ trợ, credentials, profiles, region/output format | 10/11/2025 | 10/11/2025 | <https://000011.awsstudygroup.com/1-introduce/> |
| 3 | - Cài đặt **AWS CLI v2** trên máy (Windows/Ubuntu) <br> - Kiểm tra phiên bản `aws --version` | 11/11/2025 | 11/11/2025 | <https://000011.awsstudygroup.com/3-installcli/> |
| 4 | - Cấu hình CLI bằng `aws configure` (Access Key, Secret Key, region, output) <br> - Tạo và dùng nhiều profile (`--profile`) <br> - Kiểm tra cấu hình (`aws configure list`, `list-profiles`) | 12/11/2025 | 12/11/2025 | <https://000011.awsstudygroup.com/3-installcli/> |
| 5 | - Thực hành kiểm tra tài nguyên qua CLI (describe/list) và đọc output (`json/text/table`) <br> - Thực hành với **Amazon S3**: tạo bucket, liệt kê buckets/objects, xóa object, xóa bucket | 13/11/2025 | 13/11/2025 | <https://000011.awsstudygroup.com/4-infras/> <br> <https://000011.awsstudygroup.com/5-s3/> |
| 6 | - Thực hành với **IAM**: tạo group, tạo user, add user vào group; tạo & xóa access key <br> - Thực hành với **VPC**: tạo VPC/subnets; tạo/attach Internet Gateway; tạo route table, thêm route, associate route table | 14/11/2025 | 14/11/2025 | <https://000011.awsstudygroup.com/7-iam/> <br> <https://000011.awsstudygroup.com/8-network/> |
| 7 | - Tạo **EC2 bằng AWS CLI**: tạo key pair, security group, mở SSH, chạy instance, lấy public IP, SSH vào instance, terminate instance <br> - Đọc phần **Troubleshooting**: lỗi hay gặp khi dùng CLI và tham chiếu xử lý <br> - Cleanup tài nguyên đúng thứ tự (SG → Subnet → Route table → Detach IGW → Delete IGW → Delete VPC) | 15/11/2025 | 15/11/2025 | <https://000011.awsstudygroup.com/9-ec2/> <br> <https://000011.awsstudygroup.com/10-troubleshoot/> <br> <https://000011.awsstudygroup.com/11-cleanup/> |

### Kết quả đạt được tuần 11:

* Cài đặt thành công **AWS CLI v2** và xác minh hoạt động bằng `aws --version`.

* Cấu hình được AWS CLI với:
  * Access Key / Secret Key
  * Region mặc định
  * Output format
  * Biết cách tạo và chuyển đổi nhiều **profiles** (`default`, profile tùy chỉnh).

* Thực hành thao tác quản trị AWS bằng CLI thay cho console, bao gồm các nhóm lệnh phổ biến:
  * `aws <service> describe-*`, `list-*`, `get-*` để kiểm tra tài nguyên
  * Biết tận dụng output `json/text/table` để đọc kết quả nhanh.

* Thao tác được với **Amazon S3** bằng CLI:
  * Tạo bucket (`aws s3 mb`)
  * Liệt kê buckets/objects (`aws s3 ls`)
  * Xóa object/bucket (`aws s3 rm`, `aws s3 rb`)

* Thao tác được với **IAM** bằng CLI:
  * Tạo group, tạo user, add user vào group
  * Tạo và xóa access key theo nhu cầu thực hành

* Dựng được hạ tầng mạng cơ bản bằng **VPC/IGW/Route Table** qua CLI và hiểu luồng để subnet ra Internet.

* Tạo được **EC2 instance** bằng CLI và kết nối SSH, sau đó terminate instance khi hoàn tất.

* Biết quy trình **cleanup** tài nguyên đúng thứ tự để tránh lỗi phụ thuộc và hạn chế phát sinh chi phí.
