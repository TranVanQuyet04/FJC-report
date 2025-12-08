---
title: "Sự kiện 2"
# date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---

# Báo cáo tóm tắt: “BUILDING AGENTIC AI – Context Optimization with Amazon Bedrock”

### Mục tiêu sự kiện

- Cung cấp hành trình có cấu trúc về **Agentic AI**, từ kiến trúc tổng quan đến triển khai thực hành
- Giới thiệu các khái niệm cốt lõi để xây dựng AI agent tự chủ bằng **Amazon Bedrock**
- Chia sẻ các use case thực tế cho **agentic workflows** trên AWS
- Trình bày các cách tiếp cận về **agentic orchestration** và **tối ưu ngữ cảnh (context optimization)** (phiên L300)
- Tạo điều kiện học thực hành thông qua **workshop** và cơ hội networking với chuyên gia

### Diễn giả

- **Nguyen Gia Hung** – Head of Solutions Architect
- **Kien Nguyen** – Solutions Architect
- **Viet Pham** – Founder & CEO
- **Thang Ton** – Co-Founder & COO
- **Henry Bui** – Head of Engineering
- **Kha Van** – Community Leader

### Nội dung nổi bật

#### Tổng quan sự kiện & thông tin tổ chức
- **Ngày:** **05/12/2025**
- **Địa điểm:** **Tầng 26, Bitexco Financial Tower**, TP. Hồ Chí Minh, Việt Nam
- **Chủ đề/Tagline:** Xây dựng AI agents tự chủ với Amazon Bedrock thông qua kỹ thuật thực hành và use case thực tế

#### AWS Bedrock Agent Core
- Giới thiệu các “khối nền tảng” cho hệ thống agentic trên Bedrock:
  - Lựa chọn foundation model phù hợp
  - Tích hợp tool / function để agent có thể thực thi hành động
  - Guardrails và ràng buộc để tăng an toàn và độ tin cậy
  - Khái niệm tracing và evaluation nhằm sẵn sàng cho vận hành production

#### [Use Case] Building Agentic Workflow on AWS
- Minh hoạ cách agentic workflow được áp dụng vào các kịch bản thực tế:
  - Thực thi nhiệm vụ nhiều bước thay vì chỉ hỏi–đáp một lượt
  - Vòng lặp retrieval + reasoning + action
  - Checkpoint human-in-the-loop cho các thao tác có tác động lớn

#### CloudThinker Agentic Orchestration & Context Optimization (L300)
- Giải thích vì sao **chất lượng ngữ cảnh (context)** ảnh hưởng mạnh tới độ đúng, độ trễ và chi phí
- Các hướng tiếp cận tối ưu context:
  - Giữ context “tối thiểu nhưng đủ” để giảm nhiễu và giảm hallucination
  - Tách bạch short-term context và long-term memory/knowledge
  - Dùng lọc theo metadata (phạm vi, độ mới, độ liên quan) để cải thiện retrieval
  - Áp chính sách cho context (allowlist, redaction, kiểm soát truy cập)

#### CloudThinker Hack: Hands-on Workshop
- Hướng dẫn người tham gia xây dựng một agentic flow:
  - Xác định mục tiêu → thiết kế bước → tích hợp tools → test và lặp
- Tập trung vào cách debug và cải thiện hành vi agent:
  - Kiểm tra prompt và tool calls
  - Xác minh kết quả retrieval và giảm context bloat
  - Thêm ràng buộc và kiểm tra an toàn

#### Networking & trao đổi với chuyên gia
- Kết nối với chuyên gia và người tham dự để thảo luận:
  - Các ràng buộc triển khai thực tế (security, governance, kiểm soát chi phí)
  - Observability (logging, tracing) và chiến lược đánh giá chất lượng
  - Cách tích hợp agent vào workflow kỹ thuật hiện tại

### Điểm rút ra chính

#### Tư duy về Agentic AI
- Agentic AI không chỉ là chatbot: cần **orchestration**, **tool usage**, **memory**, và **guardrails**
- Context là “đòn bẩy” quan trọng quyết định chất lượng đầu ra và chi phí vận hành

#### Hướng tiếp cận kỹ thuật
- Phân tách trách nhiệm rõ ràng:
  - Planner/orchestrator vs tools/actions vs memory/retrieval vs guardrails
- Best practices cho context optimization:
  - Giảm context không liên quan để giảm rủi ro hallucination
  - Cải thiện retrieval bằng lọc và cấu trúc dữ liệu
  - Tăng traceability để debug và audit

#### Triển khai có trách nhiệm
- Ưu tiên human-in-the-loop cho các thao tác rủi ro cao (ops, security, triển khai)
- Xác định metric thành công (accuracy, latency, cost) và đánh giá liên tục

### Ứng dụng vào công việc

- Prototype một agent nội bộ để hỗ trợ:
  - Triage sự cố, hướng dẫn theo runbook, tóm tắt log
  - Q&A dựa trên tài liệu nội bộ (retrieval + tổng hợp)
- Áp dụng context optimization:
  - Siết phạm vi retrieval và giảm prompt bloat
  - Dùng memory có cấu trúc và checkpoint kiểm tra/validate
- Cải thiện governance:
  - Thêm guardrails cho tool execution
  - Thiết lập quy trình phê duyệt cho hành động quan trọng
  - Bật logging/tracing cho compliance và troubleshooting

### Trải nghiệm sự kiện

- Sự kiện cung cấp góc nhìn thực tế end-to-end về xây dựng hệ thống agentic, kết nối giữa kiến trúc và triển khai.
- Phiên L300 giúp làm rõ cách tối ưu context cải thiện độ tin cậy và hiệu quả chi phí.
- Phần workshop thực hành củng cố best practices về thiết kế, kiểm thử và debug agentic workflows.
- Networking giúp liên hệ các khái niệm với ràng buộc triển khai thực tế và chiến lược áp dụng.

#### Bài học rút ra
- Chất lượng context quan trọng không kém lựa chọn model khi xây agent
- Cần xem agent như hệ thống production: tool usage an toàn, audit và evaluation là bắt buộc
- Human-in-the-loop vẫn rất cần cho các hành động tự chủ có tác động lớn
- Lặp nhanh theo chu trình (trace → chẩn đoán → tinh chỉnh) là cách nhanh nhất để cải thiện hành vi agent

#### Một số ảnh sự kiện
<img src="/images/4-Events/ev2-1.jpg" alt="Hình ảnh văn phòng" />
<img src="/images/4-Events/ev2-2.jpg" alt="Mặt của tôi" />
