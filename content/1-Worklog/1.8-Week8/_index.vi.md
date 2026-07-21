---
title: "Báo cáo công việc Tuần 8"
date: 2026-02-06
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu Tuần 8:
* Triển khai cơ chế mã hóa dữ liệu lưu trữ trên đám mây bằng cách khởi tạo và quản lý các khóa mã hóa tùy chỉnh.
* Cấu hình và triển khai một Amazon S3 Bucket an toàn, tích hợp tính năng mã hóa phía máy chủ sử dụng AWS KMS (SSE-KMS).

### Các công việc đã thực hiện trong tuần:
* **AWS Key Management Service (KMS):** Khởi tạo, phân quyền và triển khai Khóa đối xứng do khách hàng quản lý (Customer Managed Symmetric Key), bao gồm việc kích hoạt quy tắc tự động xoay vòng khóa định kỳ hàng năm.
* **Cấu hình Amazon S3:** Xử lý lỗi trùng tên trên hệ thống toàn cầu để khởi tạo thành công một S3 Bucket hoàn toàn mới với tên `kms-key-s3-03072026` tại vùng `sa-east-1`, tùy chỉnh quyền sở hữu đối tượng và cấu hình quyền truy cập công khai.
* **Tải dữ liệu & Thực thi mã hóa:** Thực hiện quy trình upload tệp tin thực tế (`klasjfhs.jpg`), cấu hình phân tầng lưu trữ (Storage class), bật thuật toán kiểm tra toàn vẹn dữ liệu (Checksum) và áp dụng cấu hình mã hóa khóa KMS đã tạo.

### Kết quả đạt được trong Tuần 8:

#### 1. Khởi tạo và cấu hình AWS Key Management Service (KMS)
* **Tạo khóa do khách hàng quản lý:** Thao tác thành công quy trình tạo Khóa đối xứng (Symmetric Key) dùng để mã hóa và giải mã dữ liệu, đặt tên định danh (Alias) cho khóa là `kms-key-encrypt-decrypt` (`image_f7d62b.png`, `image_f7dcee.png`).
* **Phân quyền quản lý khóa:** Chỉ định quyền quản trị khóa cho role `kms-key-role` và thiết lập chính sách bảo mật khóa (Key Policy) tương ứng (`image_f7d92a.png`, `image_f7da02.png`).
* **Cấu hình xoay vòng khóa:** Nâng cao tính bảo mật cho vật liệu mã hóa bằng cách kích hoạt tính năng **Tự động xoay vòng khóa (Automatic Key Rotation)** với chu kỳ định kỳ là **365 ngày** (`image_f7dda7.png`, `image_f7e0ca.png`).

#### 2. Xử lý trùng tên & Khởi tạo Amazon S3 Bucket (`kms-key-s3-03072026`)
* **Khắc phục lỗi hệ thống:** Trong lần thử đầu tiên, hệ thống báo lỗi `BucketAlreadyExists` do tên bucket bị trùng trên toàn cầu (`image_f83ee3.png`). Đã xử lý nhanh bằng cách thêm hậu tố ngày tháng (`03072026`) để đảm bảo tính duy nhất.
* **Khởi tạo thành công:** Tạo mới thành công bucket với tên **`kms-key-s3-03072026`** tại vùng **South America (São Paulo) sa-east-1** (`image_f8424c.png`, `image_f84346.png`).
* **Thiết lập quyền truy cập:** Bật tính năng quản lý danh sách truy cập (ACLs), gán quyền sở hữu đối tượng cho **Object writer** và tắt tính năng "Block *all* public access" để chuẩn bị cho các kịch bản kiểm thử dữ liệu ngoại vi (`image_f83e6b.png`).

#### 3. Tải tệp tin lên hệ thống & Xác thực mã hóa bảo mật
* **Tải tệp tin lên S3:** Thực hiện tải một tệp tin mẫu có tên `klasjfhs.jpg` (dung lượng 14.9 KB) lên thư mục gốc của bucket vừa tạo (`image_f84706.png`, `image_f84a8a.png`).
* **Phân tầng lưu trữ:** Chỉ định tệp tin thuộc lớp lưu trữ **Standard (Tiêu chuẩn)** để đảm bảo tần suất truy cập cao và tối ưu tốc độ phản hồi trên nhiều Availability Zones (`image_f84abf.png`).
* **Áp dụng khóa mã hóa KMS:**
  * Tại mục Server-side encryption, chọn **"Specify an encryption key"** và kích hoạt quyền ghi đè thiết lập mặc định **"Override bucket settings for default encryption"** (`image_f84ac8.png`).
  * Chọn phương thức mã hóa **SSE-KMS** và chỉ định chính xác ID của Khóa KMS đã tạo ở bước trước (khóa có mã ARN kết thúc bằng `3609742e-1fff-452b-93b9-c0164008c405`) (`image_f84ac8.png`, `image_f84d71.png`).
  * Kích hoạt tính năng **Bucket Key** để tối ưu hóa chi phí, giảm số lượng yêu cầu gọi API (API calls) từ S3 sang AWS KMS (`image_f84d71.png`).
* **Kiểm tra tính toàn vẹn dữ liệu:** Bật tính năng kiểm tra mã lỗi và chọn thuật toán **CRC64NVME** (được khuyến nghị) nhằm tự động xác thực dữ liệu không bị thay đổi hoặc lỗi trong quá trình truyền tải (`image_f84d71.png`).
* **Kết quả thực thi:** Quá trình tải lên hoàn tất thành công, không gặp bất kỳ lỗi nào. Giao diện AWS trả về thông báo trạng thái màu xanh **"Upload succeeded"** xác nhận tệp tin đã được lưu trữ an toàn kèm mã hóa khóa KMS (`image_f84d91.png`).