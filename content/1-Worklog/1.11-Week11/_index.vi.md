---
title: "Worklog Tuần 11"
date: 2026-01-07
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---


### Mục tiêu tuần 11:
* Khởi tạo cơ sở hạ tầng tầng lưu trữ trên Amazon S3 để làm Data Lake cho dự án.
* Thiết lập cấu trúc thư mục chuẩn hóa để lưu trữ các tầng dữ liệu khác nhau.
* Tải lên các dữ liệu cấu hình/meta ban đầu phục vụ cho các tiến trình xử lý dữ liệu tiếp theo.

### Các công việc cần triển khai trong tuần này:
*  Tạo một Amazon S3 bucket mới đóng vai trò là kho lưu trữ Data Lake tập trung.
*  Xây dựng cấu trúc thư mục tiêu chuẩn (`data/` và `reference_data/`) bên trong bucket.
*  Tải tệp định nghĩa schema/metadata ban đầu vào thư mục reference.

### Kết quả đạt được tuần 11:

#### 1. Khởi tạo Data Lake Bucket
* **Tên Bucket:** `asg-datalake-tuan-2026`
* **Khu vực (Region):** South America (Sử dụng cụm server São Paulo) `sa-east-1`
* **Trạng thái:** Khởi tạo thành công với các thiết lập quyền truy cập riêng tư (private) tiêu chuẩn.

#### 2. Thiết lập cấu trúc thư mục
Hai thư mục logic chính đã được tạo bên trong bucket để phân tách rõ ràng các loại dữ liệu:
* `data/`: Thư mục dành riêng cho các tập dữ liệu thô và dữ liệu vận hành được đẩy về.
* `reference_data/`: Thư mục dành riêng cho các bảng tra cứu tĩnh, tệp cấu hình và siêu dữ liệu (metadata).

#### 3. Thu thập và lưu trữ dữ liệu vào hệ thống
* **Đường dẫn đích:** `s3://asg-datalake-tuan-2026/reference_data/`
* **Tệp đã tải lên:** `tracks_list.json` (Dung lượng: 8.7 KB, Định dạng: `application/json`)
* **Trạng thái tải lên:** Thành công 100%, không xảy ra lỗi.

### Đánh giá:
*  Đã hoàn thành việc triển khai kiến trúc tầng lưu trữ dữ liệu trên Amazon S3.
*  Kiểm tra tính toàn vẹn của luồng tải dữ liệu thành công thông qua tệp JSON ban đầu.
*  Môi trường lưu trữ đã sẵn sàng để tích hợp với các bộ thu thập dữ liệu (data crawlers) và các dịch vụ phân tích ở các giai đoạn sau.
