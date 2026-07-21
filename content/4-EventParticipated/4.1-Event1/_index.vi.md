---
title: "Event 1"
date: 2026-30-05
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---


# Bài thu hoạch “Mini meetup”

### Tổng Quan Về Sự Kiện Đã Tham Gia

Vào ngày 30/05/2026 vừa qua, tôi đã có cơ hội tham dự chương trình Mini meetup với tư cách là một khán giả và người quan sát học hỏi. Đây là một chương trình được tổ chức nhằm để rèn sự mạnh dạng dám nghĩ dám làm , dám trình bày quan điểm cá nhân, dám phản biện , với chủ đề mà mình muốn chia sẻ nhằm hiểu nhau hơn và phát triển cùng nhau cùng với Amazon Web Services (AWS).

**Thông tin chung:**
* **Thời gian:** 09:00, ngày 30 tháng 05 năm 2026
* **Địa điểm:** Tầng 26, tòa nhà Bitexco, số 02 đường Hải Triều, phường Sài Gòn, thành phố Hồ Chí Minh
* **Tên hoạt động:** Mini meetup
* **Hình thức:** chia sẻ quan điểm cá nhân và phản biện 
* **Vai trò:** Người tham gia 
* **Nội dung chính:** chủ đề do người chia sẻ tự chọn  , chia sẻ kiến thức đã học và thành quả của bản thân trong quá trình thực tập . 

### Công cụ mã nguồn mở Floci (Open-Source Floci)

Floci là một trình giả lập môi trường AWS cục bộ (AWS Local Emulator) hoàn toàn miễn phí với thông điệp "Light, fluffy, and always free".

Lộ trình học tập thực tế: Diễn giả đã chia sẻ một lộ trình 3 giai đoạn rất rõ ràng dành cho người mới bắt đầu học Cloud:

Giai đoạn 1 (Phase 1 - Mind & Architecture): Làm quen với tư duy kiến trúc thông qua nền tảng tương tác AWS Cloud Quest.

Giai đoạn 2 (Phase 2 - Code & Fast Testing): Viết mã nguồn và tiến hành kiểm thử nhanh chóng, an toàn bằng cách tận dụng Open-Source Floci ngay trên máy cục bộ mà không lo phát sinh chi phí.

Giai đoạn 3 (Phase 3 - Real Deployment & Production): Triển khai hệ thống thực tế lên môi trường Real AWS.

**Bài học rút ra:** Việc biết đến Floci giúp tôi mở ra một tư duy mới trong việc tối ưu hóa quy trình kiểm thử phần mềm, cho phép thử nghiệm các tính năng Cloud một cách nhanh chóng mà không gặp áp lực về mặt ngân sách trên tài khoản AWS thật.

### Dự án Hackathon: Hệ thống xác thực giọng nói AI - SynthHunter

công nghệ AI hiện nay có thể giả mạo giọng nói để vượt qua các lớp bảo mật truyền thống, tạo ra các rủi ro lớn về lừa đảo (fraud) và tuân thủ pháp lý.

Giải pháp áp dụng: Nhóm tác giả đã mang đến giải pháp SynthHunter – một hệ thống phân loại âm thanh thông minh nhằm xác định xem các đoạn ghi âm là do con người nói (HUMAN), do trí tuệ nhân tạo tạo ra (AI GENERATED), hay cần phải xem xét thêm (NEEDS REVIEW).

Kiến trúc cốt lõi: Hệ thống vận hành dựa trên cơ chế phát hiện 3 trụ cột (Three-Pillar Detection Engine):

Speech Dynamics: Sử dụng mô hình XLS-R.

Encoder Behavior: Sử dụng giải pháp Whisper.

Temporal Rhythm: Phân tích nhịp điệu và khoảng dừng khi nói (Pause Analysis).

**Bài học rút ra:** Chủ đề này giúp tôi thấy được tính thực chiến cao của các giải pháp bảo mật ứng dụng AI, đồng thời hiểu thêm về cách kết hợp các mô hình phân tích âm thanh tiên tiến để giải quyết một lỗ hổng an ninh mạng nhức nhối hiện nay.

### Kế hoạch dịch chuyển hạ tầng của dự án "Tử vi Đại Việt"

đây là một ứng dụng giải mã vận mệnh và thấu hiểu bản ngã đã có sản phẩm chạy thực tế (Website, Facebook, Instagram) và đang lên kế hoạch tối ưu hóa hệ thống bằng cách dịch chuyển hạ tầng lên nền tảng đám mây (Cloud Migration).

So sánh cấu trúc hạ tầng (Current Stack vs AWS infra migration):

Hạ tầng hiện tại: Hệ thống sử dụng mô hình truyền thống với Backend/Frontend chạy trên máy chủ ảo VPS (Nginx + PM2), lưu trữ dữ liệu bằng MySQL, gọi API của OpenAI (GPT-4.5) để xử lý logic thông minh và dùng Redis làm bộ nhớ đệm.

Hạ tầng mục tiêu dịch chuyển lên AWS: Dự án hướng tới cấu trúc bền vững hơn bằng cách chuyển sang chạy Backend/Frontend trên Amazon ECS và Amplify Hosting; đồng thời chuyển cơ sở dữ liệu sang Amazon RDS. Đặc biệt, phần xử lý AI sẽ được thay thế bằng Amazon Bedrock để tối ưu hóa việc tích hợp LLM, kết hợp dùng Amazon ElastiCache để tăng tốc độ truy xuất và CloudWatch/Lambda để vận hành các tác vụ ngầm.

**Bài học rút ra:** Đây là một case study thực tế vô cùng giá trị đối với tôi. Nó giúp tôi hiểu rõ quy trình tư duy của một kỹ sư khi cần chuyển đổi một hệ thống từ máy chủ truyền thống sang môi trường AWS nhằm đạt được tính sẵn sàng cao, bảo mật và khả năng mở rộng lâu dài.

### Không Khí Thảo Luận Và Hoạt Động Phản Biện

Bên cạnh nội dung chuyên môn phong phú, điểm làm nên sức hút của buổi Mini meetup chính là không gian tương tác mở và hoạt động phản biện trực tiếp sau mỗi bài chia sẻ:

Tinh thần dám nghĩ, dám nói: Các diễn giả thực tập sinh đã thể hiện tinh thần rất tự tin khi trình bày quan điểm cá nhân. Họ không chỉ nói về những thành công mà còn thẳng thắn chia sẻ những khó khăn, những lỗi sai thực tế gặp phải trong quá trình cấu hình và vận hành hệ thống.

Phản biện văn minh và đa chiều: Các câu hỏi chất vấn từ phía khán giả và ban cố vấn đã giúp đẩy sâu tính chuyên môn của các chủ đề. Quá trình tranh luận này không chỉ giúp người thuyết trình tìm ra những điểm cần tối ưu trong kiến trúc của mình, mà còn giúp người tham gia quan sát như tôi rèn luyện được tư duy phân tích, nhìn nhận một vấn đề kỹ thuật dưới nhiều góc độ khác nhau.

### Những Thu Hoạch Và Định Hướng Cho Bản Thân

Sau khi kết thúc buổi Mini meetup, tôi đã tích lũy được những bài học quý báu cho hành trình phát triển của bản thân:

Về mặt kiến thức: Tôi hiểu được mối liên hệ chặt chẽ giữa việc giả lập môi trường phát triển (qua công cụ như Floci) trước khi tiến hành cấu hình hạ tầng thực tế trên hệ sinh thái Cloud của AWS (như ECS, RDS, Bedrock).

Về mặt kỹ năng mềm: Đúng như mục đích ban đầu của sự kiện, tôi nhận ra tầm quan trọng của việc dám bảo vệ quan điểm cá nhân và kỹ năng giao tiếp. Một kỹ sư công nghệ không chỉ cần giỏi chuyên môn, mà còn phải biết cách diễn đạt, thuyết trình giải pháp của mình sao cho mạch lạc và thuyết phục được người nghe.

Định hướng ứng dụng: Những kiến thức về mô hình thiết kế mạng, kết nối cơ sở dữ liệu và chuyển đổi hạ tầng đám mây này sẽ được tôi nghiên cứu sâu hơn để áp dụng vào các dự án, bài tập lớn và đồ án công nghệ sắp tới tại trường học.

## Bài Học Rút Ra 
buổi Mini meetup diễn ra tại tầng 26 tòa nhà Bitexco là một chương trình vô cùng bổ ích và giàu giá trị thực tiễn. Trải nghiệm tham gia sự kiện giúp tôi mở rộng tầm mắt về cách ứng dụng linh hoạt các dịch vụ AWS vào các bài toán thực tế từ giả lập, bảo mật AI cho đến di trú hạ tầng. Quan trọng hơn hết, tinh thần dám nghĩ, dám làm và phản biện văn minh từ buổi chia sẻ đã truyền cho tôi nguồn cảm hứng lớn để tiếp tục nỗ lực học hỏi, tự tin khẳng định bản thân trên con đường định hướng trở thành một kỹ sư công nghệ trong tương lai.
