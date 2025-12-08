---
title: "Tăng cường kiểm soát an ninh mạng: Quản lý luồng (Flow) với AWS Network Firewall"
date: "2025-04-09"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

<!-- {{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn (kể cả warning này).
{{% /notice %}} -->

<!-- # Tăng cường kiểm soát an ninh mạng: Quản lý luồng (Flow) với AWS Network Firewall -->

**AWS Network Firewall:** Một dịch vụ firewall được quản lý (managed), dạng **stateful** và có **IDS/IPS**, cho phép áp dụng các quy tắc bảo mật để kiểm soát lưu lượng mạng trong VPC một cách chi tiết.

**Bối cảnh vấn đề:** Khi một flow được firewall cho phép, quyết định đó có thể vẫn có hiệu lực trong suốt vòng đời của flow. Khi cập nhật rules (ví dụ: từ rộng → chặt), các flow chạy lâu (long-running) có thể vẫn tiếp tục theo quyết định cũ nếu không có hành động can thiệp.

**Các khả năng mới được giới thiệu:**
- **Flow capture:** Cung cấp khả năng quan sát các flow đang hoạt động theo thời điểm (point-in-time) để giám sát và xử lý sự cố.
- **Flow flush:** Cho phép kết thúc/loại bỏ trạng thái flow một cách chọn lọc (một số flow hoặc tất cả) để áp lại policy hoặc cô lập traffic đáng ngờ.

**Cách truy cập:** Có sẵn trên **AWS Management Console** và **AWS Network Firewall API**.

---

## Thuật ngữ

**Active flow:** Một kết nối mạng đang được theo dõi, được nhận diện bởi **5-tuple** (IP nguồn, IP đích, cổng nguồn, cổng đích và giao thức) và **không ở trạng thái CLOSED** (ví dụ TCP NEW hoặc ESTABLISHED).

**Flow filter:** Một tập tham số để match các active flows theo một hoặc nhiều tiêu chí (IP nguồn/đích, cổng, giao thức). Một filter có thể match nhiều flow.

**Flow capture:** Một thao tác của firewall tạo **ảnh chụp (snapshot) tại một thời điểm** của các active flows dựa trên filter(s). Dùng để quan sát, phân tích sự kiện bảo mật và kiểm tra flow trước khi flush.

**Flow flush:** Một thao tác của firewall **flush** các active flows được chọn khỏi flow table dựa trên filter(s). Sau khi flush, các gói tin tiếp theo sẽ được coi là **midstream** và được đánh giá lại theo **stream exception policy**.

---

## Tổng quan quy trình 

**Công cụ kiểm tra:** AWS Network Firewall sử dụng **Suricata** để kiểm tra stateful và duy trì trạng thái flow trong **flow table**.

**Các kịch bản flush thường gặp:**
- **Flush toàn bộ:** Xóa tất cả active flows (bảo trì/troubleshooting).
- **Flush chọn lọc:** Xóa các flow mục tiêu (cập nhật policy, traffic đáng ngờ) theo IP/cổng/giao thức.

**Chế độ vận hành:**
- **Capture → Flush:** Capture flow trước, xem kết quả, rồi flush các flow match.
- **Flush trực tiếp:** Flush ngay bằng các filter đã chỉ định.

**Theo dõi:** Trạng thái và chi tiết thao tác có thể xem trong **Firewall operation history**.

---

## Điều hướng trên Console

**Bước 1:** Mở **Amazon VPC console** → **Network Firewall** → **Firewalls**  
**Bước 2:** Chọn một firewall  
**Bước 3:** Trong mục **Firewall operations**, dùng:
- **Configure flow capture**
- **Configure flow flush**

<img src="/images/3-Blogs/bl1-1.png" alt="Blog 1" />

---

## Flow Capture

**Mục tiêu (ví dụ):** Xác định các flow đang hoạt động từ `10.0.1.0/24` → `10.0.2.0/24` trên **TCP port 80**, sau đó flush các flow này.

**Thiết lập mạng:** Lưu lượng giữa hai subnet được định tuyến qua AWS Network Firewall để kiểm tra.

<img src="/images/3-Blogs/bl1-2.png" alt="Blog 2" />

### Bắt đầu capture trên console

**Thao tác:** Chọn **Configure flow capture** (từ Figure 1).  
**Availability Zone:** Chọn AZ (bắt buộc theo mỗi operation).  
**Trường bắt buộc:** Cần ít nhất một trong hai: **Source address** hoặc **Destination address**.  
**Trường tuỳ chọn:**
- **Minimum age of flow**
- **Source port**
- **Destination port**
- **Protocol** (ICMP, TCP, UDP, IPv6-ICMP, SCTP)

**Bộ lọc:** Bấm **Add filter** (tối đa **20** filter; theo full hoặc partial 5-tuple).  
**Thực thi:** Bấm **Start capture**.

**Ghi chú hiệu năng:** Filter càng cụ thể thì thao tác thường chạy càng nhanh.

<img src="/images/3-Blogs/bl1-3.png" alt="Blog 3" />

---

### Kết quả capture

**Đầu ra:** Operation hiển thị các flows được capture theo filter(s).

<img src="/images/3-Blogs/bl1-4.png" alt="Blog 4" />

---

## Flow Flush

**Phạm vi:** Flush flows dựa trên full hoặc partial 5-tuple filters.

### Tuỳ chọn 1: Capture rồi flush

**Thao tác:** Từ kết quả capture (Figure 4), chọn **Configure flow flush** để dùng lại các filter.  
**Thực thi:** Bấm **Start flush**.

<img src="/images/3-Blogs/bl1-5.png" alt="Blog 5" />

---

### Tuỳ chọn 2: Flush trực tiếp

**Thao tác:** Trong **Firewall operations** (Figure 1), chọn **Configure flow flush**.  
**Thuộc tính filter:** Cấu hình tương tự capture (các trường filter như nhau).  
**Thực thi:** Bấm **Start flush**.

**Đầu ra:** Sau khi hoàn tất, các flow đã flush sẽ được hiển thị.

<img src="/images/3-Blogs/bl1-6.png" alt="Blog 6" />

---

## Xác minh & Ghi log

**Hành vi reconnect:** Sau khi flush, client thường sẽ cố gắng **kết nối lại**. Các lần retry này có thể xuất hiện như flow mới trong các lần capture sau.

**Giảm nhiễu:** Dùng **Minimum age** để tránh bị “rác” bởi các retry flows vừa tạo.

**Flow logs:** Nếu bật flow logs, các bản ghi cho flow bị flush có thể thể hiện trường `reason = flushed` và trạng thái cuối trước khi flush.

```json
{
  "reason": "flushed",
  "last_state": "ESTABLISHED"
}
```

<img src="/images/3-Blogs/bl1-7.png" alt="Blog 7" />

---

## Lịch sử thao tác firewall 

**Lưu giữ:** Hiển thị các thao tác capture/flush trong **12 giờ** gần nhất theo firewall và AZ.

**Tự xoá:** Các thao tác cũ hơn 12 giờ sẽ bị xoá tự động.

**Xem chi tiết:** Bấm vào **operation ID** để xem chi tiết capture/flush.

<img src="/images/3-Blogs/bl1-8.png" alt="Blog 8" />

---

## Những điều cần biết 

**Quy tắc đồng thời:** Mỗi AZ trên mỗi firewall chỉ chạy được **một** operation (capture hoặc flush) tại một thời điểm.

**Nhiều AZ:** Nếu firewall endpoints triển khai ở nhiều AZ, có thể chạy capture/flush **song song** trên các AZ khác nhau.

**Minimum age:** Hữu ích để tìm/flush flow chạy lâu (ví dụ **300 giây** = flow active ≥ 5 phút).

**Stream exception policy:** Sau flush, packet sẽ được đánh giá theo **stream exception policy** của firewall policy (thường khuyến nghị: **reject**).

**Thực thi phân tán:** Capture/flush có thể hơi khác nhau giữa các firewall hosts do operation chạy “roll” trên hạ tầng phân tán.

**Hỗ trợ IPv4/IPv6:** Tính năng hỗ trợ cả IPv4 và IPv6 flows.

**Audit:** AWS CloudTrail ghi nhận capture/flush dưới dạng **Management events**.

**Chi phí:** Không tính thêm phí; được bật mặc định.

---

## Kết luận 

**Tóm tắt:** Flow capture cung cấp khả năng quan sát các luồng mạng đang hoạt động theo thời điểm, trong khi flow flush cho phép loại bỏ trạng thái flow một cách chọn lọc để áp lại policy bảo mật đã cập nhật hoặc cô lập kết nối đáng ngờ. Kết hợp lại, hai tính năng này cải thiện giám sát, troubleshooting, phản ứng sự cố và đảm bảo thực thi policy nhất quán trên các kết nối đang hoạt động.

---