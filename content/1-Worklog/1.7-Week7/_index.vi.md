---
title: "Worklog Tuần 7"
date: 2026-05-26
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:

* Nghiên cứu và triển khai giải pháp quản lý danh tính, phân quyền (IAM) kết hợp với giải pháp mã hóa dữ liệu lưu trữ trên AWS cloud.
* Xây dựng cấu trúc phân quyền an toàn theo nguyên tắc đặc quyền tối thiểu (Least Privilege) cho nhóm người dùng và dịch vụ lưu trữ Amazon S3.

### Các công việc cần triển khai trong tuần này:

* **Quản lý phân quyền (IAM):** Thiết lập Customer Managed Policy, IAM Role cho dịch vụ, IAM User, và IAM User Group trên AWS Console.
* **Mã hóa dữ liệu (KMS):** Khởi tạo và cấu hình khóa đối xứng Customer Managed Key (KMS) để chuẩn bị tích hợp mã hóa mặc định cho S3 Bucket.

### Kết quả đạt được tuần 7:

#### 1. Hoàn thành thiết lập Identity and Access Management (IAM)

* **Tạo Custom Policy & Role:** Khởi tạo thành công `kms-key-policy` và gán vào IAM Role mang tên `kms-key-role`. Role này cấu hình Trust Relationship cho phép dịch vụ Amazon S3 (`s3.amazonaws.com`) thực thi.
* **Quản lý Nhóm người dùng (User Group):** Tạo User Group mang tên `GroupLimit` và đính kèm AWS Managed Policy `AmazonS3FullAccess` để kiểm soát quyền hạn truy cập tài nguyên lưu trữ.
* **Quản lý Người dùng (IAM User):** 
  * Khởi tạo thành công IAM User mới có tên `User-S34`, kích hoạt quyền truy cập AWS Management Console bằng mật khẩu tùy chỉnh.
  * Gán người dùng `User-S34` vào nhóm `GroupLimit` để kế thừa các quyền hạn của nhóm.
  * Xuất file thông tin bảo mật đăng nhập (`credentials.csv`) và tiến hành kiểm tra đăng nhập thành công vào AWS Console với thông tin định danh mới.

#### 2. Khởi tạo và cấu hình AWS Key Management Service (KMS)

* Thực hiện các bước thiết lập khóa mã hóa đối xứng (Symmetric Key) thuộc loại Customer Managed Key.
* Cấu hình phân quyền quản trị khóa (Key Administrator) cho tài khoản quản trị hiện tại và chỉ định quyền sử dụng khóa (Key Usage Permissions) cho `kms-key-role` nhằm cho phép S3 sử dụng khóa để mã hóa/giải mã dữ liệu.