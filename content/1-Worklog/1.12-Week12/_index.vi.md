---
title: "Worklog Tuần 12"
date: 2026-05-07
weight: 2
chapter: false
pre: " <b> 1.12 </b> "
---


### Mục tiêu Tuần 12:
* Triển khai kiến trúc serverless hướng sự kiện (event-driven) sử dụng AWS Lambda để xử lý tự động hóa quy trình xử lý hình ảnh.
* Sử dụng môi trường AWS Cloud9 IDE để phát triển, đóng gói và triển khai mã nguồn serverless.
* Cấu hình tính năng S3 Event Notifications để tự động kích hoạt hàm Lambda ngay khi có hình ảnh mới được tải lên.

### Các tác vụ triển khai trong tuần:
*  Khởi tạo môi trường làm việc AWS Cloud9 để phục vụ phát triển ứng dụng serverless.
*  Tạo hàm AWS Lambda (`CreateThumbnail`) với môi trường thực thi Node.js.
*  Thiết lập bộ kích hoạt (trigger) Amazon S3 Bucket Event Notification để bắt các sự kiện `ObjectCreated`.
* Kiểm thử, tìm và khắc phục lỗi cú pháp module (`Runtime.UserCodeSyntaxError`) trong quá trình chạy thử nghiệm tích hợp cục bộ.

### Kết quả đạt được trong Tuần 12:

#### 1. Khởi tạo hàm Serverless Lambda
* **Tên hàm (Function Name):** `CreateThumbnail`
* **Môi trường thực thi (Runtime):** Node.js 18.x (Kiến trúc: `x86_64`)
* **Phương thức triển khai:** Được lập trình, đóng gói và đẩy lên trực tiếp thông qua môi trường làm việc AWS Cloud9.

#### 2. Kiểm sửa lỗi và Giải pháp kỹ thuật
* **Lỗi gặp phải:** Trong quá trình chạy thử nghiệm ban đầu, hàm Lambda đã trả về thông báo lỗi `Runtime.UserCodeSyntaxError: Cannot use import statement outside a module`. Lỗi này xảy ra do mã nguồn sử dụng cú pháp ES Module (`import`) trong khi Node.js mặc định chạy theo quy tắc CommonJS.
* **Giải pháp thực hiện:** Sửa đổi thành công file cấu hình `package.json` bên trong không gian làm việc Cloud9 bằng cách thêm thuộc tính `"type": "module"`. Sau đó tiến hành đóng gói lại mã nguồn và triển khai lại gói ứng dụng lên Lambda qua dòng lệnh terminal.

#### 3. Cấu hình sự kiện kích hoạt S3 (S3 Trigger)
* **Bucket nguồn:** `asg-datalake-tuan-2026`
* **Loại sự kiện:** `All object create events` (`s3:ObjectCreated:*`)
* **Cơ chế hoạt động:** Đã xác minh kết nối tự động thành công; bất kỳ hình ảnh nào được tải lên thư mục nguồn hiện tại đều kích hoạt luồng xử lý tạo ảnh thu nhỏ (thumbnail) của Lambda một cách mượt mà.

### Đánh giá kết quả:
*  Hoàn thành 100% việc thiết lập đường ống (pipeline) tự động xử lý hình ảnh bằng AWS Cloud9 và Lambda.
* Khắc phục thành công lỗi biên dịch module khi thực thi, đảm bảo khả năng tương thích và chạy ổn định của cú pháp ES Module.
* Hệ thống hoạt động an toàn, phản hồi các sự kiện từ S3 theo thời gian thực một cách hiệu quả và không tốn chi phí quản lý hạ tầng.