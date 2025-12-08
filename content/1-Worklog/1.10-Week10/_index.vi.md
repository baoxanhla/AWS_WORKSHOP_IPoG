---
title: "Worklog Tuần 10"
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu tuần 10:

* Biết triển khai Amazon CloudWatch giám sát hệ thống 
* Hiểu được quy trình AWS CloudTrail ghi lại toàn bộ theo dõi hoạt động chi tiết của API

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tìm hiểu về Amazon CloudWatch <br>&emsp; + Metrics <br>&emsp; + Logs <br>&emsp; + Alarms <br>&emsp; + Events <br>&emsp; + Dashboards  <br>&emsp; + AWS X-Ray | 10/11/2025   | 10/11/2025      |
| 3   | - **Thực hành**: <br>&emsp; + Tạo IAM Role, IAM policy và cấu hình EC2 Instance  <br>&emsp; + Cấu hình CloudWatch metric , logs <br>&emsp; + Kích hoạt CloudWatch Alams <br>&emsp; + Cấu hình Dashboards <br>&emsp; + Dọn dẹp tài nguyên   | 11/11/2025   | 11/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Tìm hiểu AWS CloudTrail <br>&emsp; + Trails <br>&emsp; + event: Read/Write/All <br>&emsp; + CloudTrail Insights| 12/11/2025   | 12/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Tìm hiểu AWS Amplify <br>&emsp; + Frontend <br>&emsp; + Backend <br>&emsp; + Storage <br>&emsp; + Authentication     | 13/11/2025   | 13/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Thực hành:**: Giám sát Lambda với CloudWatch và X-Ray <br>&emsp; + Host source code lên Amplify <br>&emsp; + Giám sát với CloudWatch: Gỡ lỗi với logs, tạo customer metric và tạo cảnh báo với Alarm <br>&emsp; + Giám sát với X-Ray <br>&emsp; + Dọn dẹp tài nguyên. | 14/11/2025   | 14/11/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 10:

* Triển khai cơ bản được hệ thống giám sát toàn diện với Amazon CloudWatch:

  * Metrics: Phân biệt được Metrics mặc định (như CPU, Network) và Custom Metrics (như Memory usage, Disk space - những chỉ số AWS không tự động thu thập từ bên ngoài hypervisor). Biết cách cài đặt CloudWatch Agent để đẩy các chỉ số custom này từ EC2 lên CloudWatch.
  * Quản lý Logs tập trung: Biết cách gom log từ nhiều nguồn (EC2 app logs, Lambda execution logs) về CloudWatch Logs Group để tra cứu.
  * Alarms: Thiết lập được hệ thống cảnh báo (qua email/SMS với SNS) khi hệ thống gặp sự cố (CPU quá tải, disk đầy, hoặc ứng dụng trả về nhiều lỗi ).
  * Dashboard quản trị: Xây dựng được bảng điều khiển trực quan hiển thị sức khỏe của toàn bộ hệ thống trên một màn hình duy nhất.

* Kiểm soát an ninh với AWS CloudTrail:

  * Phân biệt rõ sự khác nhau cốt lõi: CloudWatch trả lời câu hỏi "Hệ thống hoạt động thế nào?", còn CloudTrail trả lời câu hỏi "Ai đã làm gì với hệ thống?".
  * Biết cách theo dõi lịch sử API calls để phục vụ mục đích bảo mật và điều tra sự cố . Ví dụ: Tìm ra ai đã xóa nhầm Security Group hoặc ai đã tắt EC2 instance.
  * Hiểu về CloudTrail Insights để tự động phát hiện các hành vi bất thường trong tài khoản (ví dụ: đột biến số lượng API call để tạo resource).

* Triển khai ứng dụng nhanh chóng với AWS Amplify:

  * Hiểu Amplify là bộ công cụ giúp tăng tốc quy trình phát triển ứng dụng web/mobile, tự động hóa việc kết nối Frontend với các dịch vụ Backend (Auth, Storage, API).
  * Thực hành thành công quy trình CI/CD đơn giản hóa: Đẩy code lên Git -> Amplify tự động build và deploy ra môi trường Hosting.
  * Biết cách tích hợp việc giám sát (CloudWatch/X-Ray) ngay vào ứng dụng được deploy bởi Amplify để theo dõi trải nghiệm người dùng cuối.