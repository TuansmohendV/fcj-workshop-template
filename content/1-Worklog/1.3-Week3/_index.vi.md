---
title: "Worklog Tuần 3"
date: 2026-05-26
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:
- Thực hành Khởi tạo EC2 Instance trên nền tảng điện toán đám mây AWS.
- Hiểu rõ cơ chế hoạt động, cách phân chia Subnet (Public/Private) và cấu hình phân quyền truy cập an toàn cho Instance.

### Các công việc cần triển khai trong tuần này:

- **Nghiên cứu lý thuyết:** Tìm hiểu về dịch vụ Amazon EC2 (Elastic Compute Cloud), các loại Instance Types, và cơ chế bảo mật thông qua Key Pair và Security Group.
- **Cấu hình hạ tầng mạng cơ sở:** Kiểm tra và tối ưu cấu hình mạng VPC (Virtual Private Cloud), thiết lập tính năng `Auto-assign public IPv4 address` cho Public Subnet để đảm bảo Instance có thể giao tiếp với Internet.
- **Triển khai khởi tạo:** Thực hiện các bước Launch Instance: Lựa chọn Amazon Machine Image (AMI) phù hợp, cấu hình cấu hình phần cứng (vCPU, RAM, Storage), tạo mới/gắn Key Pair để phục vụ kết nối SSH an toàn.
- **Cấu hình tường lửa:** Thiết lập Inbound/Outbound Rules trong Security Group nhằm quản lý và kiểm soát lưu lượng truy cập mạng đi vào/đi ra khỏi Instance.
- **Kiểm tra và nghiệm thu:** Tiến hành kết nối từ xa vào EC2 Instance thông qua SSH/EC2 Instance Connect để kiểm tra trạng thái hoạt động của hệ thống.

### Kết quả đạt được tuần 3:

- **Khởi tạo thành công:** Triển khai thành công EC2 Instance chạy hệ điều hành Linux/Ubuntu hoạt động ổn định trên vùng môi trường mạng đã thiết lập sẵn.
- **Làm chủ cấu hình mạng:** Giải quyết triệt để lỗi phân cấp IP bằng cách cấu hình chuẩn xác tính năng tự động cấp phát Public IPv4 (`Auto-assign public IPv4`) cho Subnet, giúp hệ thống hiển thị trạng thái khả dụng một cách đồng bộ.
- **Quản trị bảo mật vững chắc:** Tạo lập thành công cặp khóa bảo mật (Key Pair) và cấu hình Security Group tối ưu, mở đúng các Port cần thiết (ví dụ: Port 22 cho SSH, Port 80/443 cho Web Traffic) giúp chặn đứng các truy cập trái phép từ bên ngoài.
- **Tối ưu hóa kỹ năng:** Nắm vững quy trình xử lý sự cố (troubleshooting) trên AWS Console, kỹ năng đọc hiểu trạng thái tài nguyên và sẵn sàng cho việc triển khai các ứng dụng thực tế lên Cloud trong các tuần tiếp theo.