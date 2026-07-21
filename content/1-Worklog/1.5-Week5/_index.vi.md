---
title: "Worklog Tuần 5"
date: 2026-05-13
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---


### Mục tiêu tuần 5:

* Khởi tạo hạ tầng mạng VPC bảo mật cho ứng dụng.
* Triển khai cơ sở dữ liệu MySQL (RDS) và máy chủ trạm làm việc (EC2 Windows).
* Cấu hình môi trường lập trình tự động và nạp dữ liệu mẫu cho hệ thống.

### Các công việc cần triển khai trong tuần này:

* Triển khai file template CloudFormation để tạo VPC, Subnets, NAT Gateway và các IAM Roles.
* Khởi tạo cơ sở dữ liệu RDS MySQL trong vùng mạng Private Subnet.
* Cấu hình máy chủ EC2 Windows Host chạy script tự động cài đặt công cụ (Java, Maven, Tomcat, IDE).
* Chạy script SQL để khởi tạo cấu trúc bảng và dữ liệu mẫu cho ứng dụng TravelBuddy.


### Kết quả đạt được tuần 5:

* **Mạng (VPC):** Tạo thành công `DevAxNetworkVPC` gồm 2 Public Subnet và 2 Private Subnet, cấu hình xong NAT Gateway để bảo mật.
* **Cơ sở dữ liệu (RDS):** Triển khai xong DB MySQL 8.0 (`db.t2.micro`) nằm trong vùng Private Subnet an toàn.
* **Máy chủ (EC2 Windows):** Khởi tạo thành công máy chủ Windows Server 2019, tự động cài đặt xong bộ công cụ lập trình (Java, Maven, Git, Tomcat, Eclipse, IntelliJ) qua script.
* **Dữ liệu mẫu:** Chạy xong script `DB.sql` tạo sẵn các bảng và dữ liệu mẫu (`flightspecial`, `hotelspecial`) cho ứng dụng TravelBuddy.
* **Bảo mật:** Cấu hình xong Security Groups mở cổng RDP (3389), MySQL (3306) và thiết lập các IAM Roles hệ thống.






