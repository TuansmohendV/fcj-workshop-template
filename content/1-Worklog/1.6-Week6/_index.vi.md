---
title: "Worklog Tuần 6"
date: 2026-05-17
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:

* Làm quen với các dịch vụ bảo vệ dữ liệu trên môi trường AWS.
* Khởi tạo thành công không gian lưu trữ và cấu hình phân quyền trên Amazon S3 để chuẩn bị tài nguyên cho quy trình triển khai AWS Backup.

### Các công việc cần triển khai trong tuần này:

* Tạo một Amazon S3 Bucket với tên gọi độc nhất trên toàn cầu (Global namespace).
* Thiết lập cấu hình thư mục con (Folder) bên trong bucket để tổ chức nơi lưu trữ dữ liệu.
* Nghiên cứu cách cấu hình quyền truy cập (Permissions), chỉnh sửa Block Public Access và thiết lập Bucket Policy bằng mã JSON.
* Chuẩn bị sẵn dữ liệu mẫu (tải các tệp cấu hình cần thiết lên S3 Bucket).

### Kết quả đạt được tuần 6:

* **Khởi tạo Amazon S3 Bucket thành công:** Tạo thành công bucket tên là `backup-lab-02072026-xyz` tại vùng South America (São Paulo) đảm bảo không bị trùng lặp trên toàn hệ thống.
* **Tổ chức cấu trúc thư mục hoàn chỉnh:** Tạo thành công thư mục con `backup-lab/` bên trong bucket.
* **Tải dữ liệu mẫu lên S3 thành công:** Tải lên thành công 2 tệp dữ liệu thử nghiệm bao gồm `lambda_function.zip` và `backup-lab.yaml` vào đúng thư mục đích với trạng thái *Succeeded (100%)*.
* **Nắm rõ cơ chế phân quyền S3:** Hiểu rõ cách xử lý xung đột bảo mật giữa tính năng *Block all public access* và đoạn mã *Bucket Policy (JSON)* khi cấu hình quyền đọc dữ liệu (`s3:GetObject`).