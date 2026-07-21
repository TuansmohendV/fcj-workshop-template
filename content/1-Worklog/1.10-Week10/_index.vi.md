---
title: "Worklog Tuần 10"
date: 2026-28-06
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---


### Mục tiêu tuần 10:

* Cấu hình và phân quyền hệ thống trên AWS IAM (Identity and Access Management) phục vụ cho dịch vụ AWS Glue.
* Đảm bảo AWS Glue có đầy đủ quyền truy cập tài nguyên S3 và quyền thực thi (`iam:PassRole`) an toàn theo nguyên tắc đặc quyền tối thiểu.

### Các công việc cần triển khai trong tuần này:

*  Tạo IAM Role mới cho dịch vụ AWS Glue.
*  Gắn các chính sách quản lý (AWS Managed Policies) cần thiết bao gồm quyền truy cập S3 toàn quyền và quyền cơ bản của Glue.
*  Tạo một Custom IAM Policy quản lý quyền `iam:PassRole`.
*  Đính kèm Custom Policy vào IAM Role để hoàn tất chuỗi phân quyền.

### Kết quả đạt được tuần 10:

#### 1. Thông tin cấu hình IAM Role (`AWSGlueServiceRoleDefault`)
* **ARN:** `arn:aws:iam::150460248067:role/AWSGlueServiceRoleDefault`
* **Creation date:** July 04, 2026, 01:31 (UTC+07:00)
* **Maximum session duration:** 1 hour
* **Trusted Entity:** AWS Service (`glue.amazonaws.com`)

#### 2. Danh sách các Permissions Policies đã gắn (3 policies)

Hệ thống đã được phân quyền đầy đủ thông qua 3 chính sách (Permissions policies):
* **`AmazonS3FullAccess`** *(AWS managed)*: Cấp toàn quyền thao tác dữ liệu (Đọc/Ghi) trên các bucket Amazon S3.
* **`AWSGlueServiceRole`** *(AWS managed)*: Cấp các quyền cơ bản mặc định để dịch vụ AWS Glue thực thi các tác vụ Crawler và Job.
* **`milo`** *(Customer managed)*: Chính sách tùy chỉnh được tạo bằng JSON nhằm cấp quyền `iam:PassRole` cho chính cấu hình Role này, cụ thể:
  ```json
  {
      "Version": "2012-10-17",
      "Statement": [
          {
              "Sid": "Statement1",
              "Effect": "Allow",
              "Action": "iam:PassRole",
              "Resource": "arn:aws:iam::150460248067:role/AWSGlueServiceRoleDefault"
          }
      ]
  }
