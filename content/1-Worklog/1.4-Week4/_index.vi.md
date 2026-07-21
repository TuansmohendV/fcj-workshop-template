---
title: "Worklog Tuần 4"
date: 2026-06-05
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

- Tìm hiểu cách sử dụng dịch vụ **AWS Billing and Cost Management** nhằm theo dõi, giám sát và kiểm soát chi phí sử dụng đám mây AWS một cách hiệu quả.
- Nắm vững quy trình thiết lập nâng cao các ngưỡng chi phí và hệ thống cảnh báo qua email tự động để đảm bảo tuân thủ ngân sách.

### Các công việc cần triển khai trong tuần này:

- Truy cập vào AWS Management Console và cấu hình ngân sách tùy chỉnh bằng tùy chọn thiết lập nâng cao Customize (advanced).
- Định nghĩa một ngưỡng ngân sách cố định lặp lại hàng tháng (Monthly recurring fixed budget) là $100.00 áp dụng cho tất cả các dịch vụ AWS.
- Cấu hình tiêu chí cảnh báo tự động để kích hoạt và gửi email thông báo đến địa chỉ chỉ định (`tuanthanhmai708@gmail.com`) khi chi phí thực tế chạm mức 80% số tiền ngân sách đã đặt.
- Kiểm tra lại toàn bộ cấu hình và hoàn tất quy trình để kích hoạt tính năng giám sát chi phí chủ động.

### Kết quả đạt được tuần 4:
- **Thực hành thành công và áp dụng các cấu hình quản lý chi phí nâng cao trên AWS:**

    - Gặt hái được kinh nghiệm thực tế trong việc thiết lập các ngân sách chi phí tùy chỉnh với các tham số chi tiết, thay vì chỉ phụ thuộc hoàn toàn vào các mẫu (templates) cơ bản.
    - Khởi tạo và triển khai thành công một ngân sách chi phí mới có tên là `Monthly` với hạn mức $100.00, bổ sung vào danh sách theo dõi chủ động bên cạnh các ngân sách đã có sẵn.
    - Cấu hình chạy tốt bộ kích hoạt ngưỡng (threshold trigger) ở mức 80% chi phí thực tế kết hợp đồng bộ trực tiếp với tùy chọn nhận thông báo qua email.
    - Tất cả các cấu hình đều được xác thực thành công và hiển thị trạng thái ổn định "Healthy" trên bảng điều khiển tổng quan Budgets, đảm bảo thiết lập hàng rào tài chính chủ động cho các tài nguyên đám mây.