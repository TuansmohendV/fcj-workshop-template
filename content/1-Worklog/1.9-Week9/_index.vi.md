---
title: "Worklog Tuần 9"
date: 2026-06-20
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9:
* Thiết lập hệ thống giám sát và ghi nhật ký tự động (Auditing & Logging) cho các thao tác trên hạ tầng đám mây AWS Cloud.
* Cấu hình lưu trữ tập trung dữ liệu CloudTrail logs vào Amazon S3 phục vụ cho công tác phân tích chuyên sâu bằng Amazon Athena.

### Các công việc cần triển khai trong tuần này:

* **Khởi tạo AWS CloudTrail:** Tạo mới một Trail giám sát tích hợp trên toàn vùng (Multi-region trail) nhằm theo dõi và kiểm tra toàn bộ hoạt động API Account.
* **Cấu hình liên kết Amazon S3:** Thiết lập đích đến cho tệp tin nhật ký (Log location) trỏ thẳng vào S3 Bucket `kms-key-s3-03072026`.
* **Phân tách & Lọc Log sự kiện:** Cấu hình chi tiết bộ lọc sự kiện bao gồm cả quản trị hệ thống (Management events) và các thao tác thay đổi cấu trúc dữ liệu bên trong Bucket (Data events).

### Kết quả đạt được tuần 9:

#### 1. Định tuyến và Khởi tạo AWS CloudTrail

* **Truy cập dịch vụ:** Sử dụng thanh công cụ tìm kiếm AWS Console điều hướng thành công từ giao diện Amazon S3 sang trang quản trị trung tâm của dịch vụ **CloudTrail** (`image_f8604f.png`).
* **Khởi tạo quy trình:** Tại danh mục điều hướng, truy cập vào phần **Trails** và chọn **Create trail** để bắt đầu chuỗi thiết lập (`image_f860b2.png`).

#### 2. Cấu hình Thuộc tính Trail (Choose Trail Attributes)

* **Đặt tên định danh:** Thiết lập tên cho chuỗi nhật ký là `kms-key-cloudtrail` để phân biệt cấu trúc quản lý (`image_f8b302.png`).
* **Lưu trữ tập trung trên S3:** 
  * Chọn tùy chọn **"Use existing S3 bucket"** để tối ưu tài nguyên lưu trữ đã có (`image_f8b302.png`).
  * Nhập chính xác tên định danh của S3 Bucket mục tiêu: `kms-key-s3-03072026` (`image_f8b302.png`).
* **Mã hóa bảo mật tệp nhật ký:** 
  * Kích hoạt thuộc tính **Log file SSE-KMS encryption** (`image_f8b302.png`).
  * Chọn **New** tại mục Customer managed AWS KMS key và đặt tên Alias cho khóa mã hóa nhật ký mới là `cloudtrail` (`image_f8b387.png`).
* **Tính năng bổ sung:** Bật trạng thái **Enabled** cho chức năng **Log file validation** nhằm bảo vệ tính toàn vẹn, chống giả mạo hoặc thay đổi trái phép đối với các tệp tin log (`image_f8b323.png` / `image_f8b387.png`).

#### 3. Cấu hình Bộ lọc Sự kiện Nhật ký (Choose Log Events)

* **Kích hoạt sự kiện quản trị (Management events):** Chọn ghi lại toàn bộ các hoạt động quản lý hạ tầng đám mây bao gồm cả hai tác vụ **Read** (Đọc/Liệt kê) và **Write** (Ghi/Khởi tạo/Xóa) (`image_f8b3c5.png`).
* **Kích hoạt sự kiện dữ liệu S3 (Data events):** 
  * Chọn nguồn dữ liệu sự kiện (Data event source) định mục cụ thể là **S3** (`image_f8b701.png`).
  * Tại phần cấu hình bộ lọc cụ thể (Individual bucket selection), tiến hành gán S3 Bucket `kms-key-s3-03072026` vào danh sách giám sát bắt buộc, theo dõi toàn bộ hành vi **Read** và **Write** của các đối tượng (Objects) bên trong (`image_f8b701.png`).

#### 4. Kiểm tra tổng thể trước khi Triển khai (Review and Create)

* **Rà soát thuộc tính Trail:** Hệ thống tổng hợp đầy đủ các thông số cốt lõi bao gồm trạng thái Multi-region: *Yes*, chức năng mã hóa SSE-KMS với khóa `cloudtrail`: *Enabled*, đường dẫn thư mục lưu trữ log được cấu hình chuẩn xác tại `kms-key-s3-03072026/AWSLogs/150460248067/` (`image_f8b70a.png`).
* **Rà soát bộ lọc log sự kiện:** Xác nhận bộ lọc bao gồm đầy đủ Management events (API activity: All) (`image_f8ba6e.png`). Trạng thái ghi nhận nhật ký (Read/Write) cho cả cấu trúc bên trong của đơn thể S3 Bucket `kms-key-s3-03072026` được kích hoạt đầy đủ (`image_f8bae8.png`). 
* Các cấu hình nâng cao khác như *Insights events*, *Network activity events*, và *Configure event aggregation* được giữ ở trạng thái mặc định hoặc không chọn cấu hình (`image_f8ba6e.png` / `image_f8bae8.png`).

#### 5. Hoàn tất khởi tạo và Trạng thái hoạt động

* **Khởi tạo thành công:** Sau khi nhấn xác nhận tạo, hệ thống hiển thị thông báo biểu tượng xanh lục **"Trail successfully created"** tại giao diện quản trị trung tâm (`image_f8bb44.png`).
* **Trạng thái vận hành:** 
  * Định danh chuỗi Trail `kms-key-cloudtrail` thuộc vùng Home region là **South America (São Paulo)** đã chính thức hoạt động (`image_f8bb44.png`).
  * Thuộc tính **Multi-region trail** hiển thị trạng thái *Yes* và cột **Status** hiển thị tích xanh **Logging** (đang tiến hành ghi log theo thời gian thực) (`image_f8bb44.png`).
  * Toàn bộ dữ liệu nhật ký đang được tự động phân tách và đẩy trực tiếp về S3 bucket đích mang tên `kms-key-s3-03072026` (`image_f8bb44.png`).