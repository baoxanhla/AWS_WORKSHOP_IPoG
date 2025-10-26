---
title: "Worklog Tuần 4"
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

* Hiểu và ứng dụng các dịch vụ lưu trữ dữ liệu trên AWS như S3, Storage Gateway, và Snow Family.
* Nắm vững các cơ chế sao lưu và khôi phục dữ liệu với AWS Backup và Disaster Recovery on AWS.
* Biết cách triển khai giải pháp lưu trữ an toàn, mở rộng và đảm bảo tính sẵn sàng cao cho hệ thống ứng dụng.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tìm hiểu Amazon Simple Storage Service (Amazon S3) <br>&emsp; + S3 Bucket <br>&emsp; + S3 Object <br>&emsp; + Access Point <br>&emsp; + Các lớp lưu trữ: Standard, Standard-IA, Intelligent-Tiering, Glacier + S3 Static Website & CORS + Control Access + Endpoint & Versioning + Object Key & Performance + Glacier: Expedited, Standard, Bulk <br> - **Thực hành:** <br>&emsp; + Tạo S3 Bucket <br>&emsp; + Upload dữ liệu lên S3 <br>&emsp; + Host static wedsite trên S3: bật tính năng static wedsite, Cấu hình Block Public Access và public object <br>&emsp; + Kiểm tra wedsite <br>&emsp; + Tăng tốc wedsite với Cloufront <br>&emsp; + Di chuyển Object và sao chép S3 Object sang region khác <br>&emsp; + Dọn dẹp tài nguyên                                             | 11/08/2025   | 11/08/2025      |
| 3   | - Tìm hiểu cách sử dụng AWS Backup để tạo ra một kế hoạch sao lưu cho các tài nguyên đang hoạt động trên AWS <br>&emsp; + Hạ tầng của AWS Backup <br>&emsp; + Backup Plan <br>&emsp; + AWS SNS (Simple Notification Service) <br> - **Thực hành:** <br>&emsp; + Tạo S3 Bucket và triển khai hạ tầng AWS Backup <br>&emsp; + Tạo Backup Plan <br>&emsp; + Thiết lập Nofication <br>&emsp; + Kiểm tra hoạt động <br>&emsp; + Dọn dẹp tài nguyên  | 12/08/2025   | 12/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Tìm hiểu Snow Family: + Snowball + Snowball Edge + Snowmobile <br> - Tìm hiểu Storage Gateway <br>&emsp; + Cổng kết nối tập tin (File Gateway) <br>&emsp; + Cổng kết nối ổ đĩa (Volume Gateway) <br>&emsp; + Cổng kết nối băng từ (Tape Gateway)  <br> - Tìm hiểu Disaster Recovery: Recovery Time Object RTO và Recovery Point Object RPO <br>&emsp; + Sao lưu và khôi phụ <br>&emsp; + Pilot Light (Active-Standby) <br>&emsp; + Low Capacity (Active-Active) <br>&emsp; + Full Capacity (Active-Active) <br> - **Thực hành:**  <br>&emsp; + Tạo Storage Gateway <br>&emsp; + Cài AWS CLI & cấu hình <br> &emsp; + Cách sử dụng AWS CLI | 13/08/2025   | 13/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Tìm hiểu EC2 cơ bản: <br>&emsp; + Instance types <br>&emsp; + AMI <br>&emsp; + EBS <br>&emsp; + ... <br> - Các cách remote SSH vào EC2 <br> - Tìm hiểu Elastic IP   <br>                  | 14/08/2025   | 15/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Thực hành:** <br>&emsp; + Tạo EC2 instance <br>&emsp; + Kết nối SSH <br>&emsp; + Gắn EBS volume                                                                                         | 15/08/2025   | 15/08/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 4:

* Hiểu AWS là gì và nắm được các nhóm dịch vụ cơ bản: 
  * Compute
  * Storage
  * Networking 
  * Database
  * ...

* Đã tạo và cấu hình AWS Free Tier account thành công.

* Làm quen với AWS Management Console và biết cách tìm, truy cập, sử dụng dịch vụ từ giao diện web.

* Cài đặt và cấu hình AWS CLI trên máy tính bao gồm:
  * Access Key
  * Secret Key
  * Region mặc định
  * ...

* Sử dụng AWS CLI để thực hiện các thao tác cơ bản như:

  * Kiểm tra thông tin tài khoản & cấu hình
  * Lấy danh sách region
  * Xem dịch vụ EC2
  * Tạo và quản lý key pair
  * Kiểm tra thông tin dịch vụ đang chạy
  * ...

* Có khả năng kết nối giữa giao diện web và CLI để quản lý tài nguyên AWS song song.
* ...


