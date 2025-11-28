---
title: "Worklog Tuần 8"
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8:

* Tự động hóa việc tạo tài nguyên bằng CloudFormation 
* Quản lý cấu hình hệ thống

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   |  - Tìm hiểu AWS CloudFormation, Cloud9 <br>&emsp; + Template: Json, Yaml <br>&emsp; + Stack <br>&emsp; + Drift Detection<br> -**Thực hành** <br>&emsp; + Sử dụng Cloud9 để tạo CloudFormation template cơ bản | 11/08/2025   | 11/08/2025      |
| 3   | - **Thực hành:** CloudFormation nâng cao: <br>&emsp; + Tạo Lambda Funtion <br>&emsp; + Tạo Stack <br>&emsp; + Kết nối EC2 instance <br>&emsp; + Ánh xạ và Stacksets <br>&emsp; + Drift Detecion <br>&emsp; + Dọn dẹp tài nguyên   | 15/08/2025   | 15/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Tìm hiểu AWS Systems Manager (SSM) <br>&emsp; + Patch Manager <br>&emsp; + Run Command <br>&emsp; + Session manager <br> - **Thực hành** <br> &emsp; + Tạo EC2 instance, IAM Role và gán IAM Role <br> &emsp; + Cấu hình Patch Manager + Run Comman <br> &emsp; + Dọn dẹp tài nguyên   | 12/08/2025   | 12/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Tìm hiểu AWS CDK <br> **Thực hành**: AWS CDK với VS Code <br>&emsp; + Tạo EC2 instance public <br>&emsp; + Cấu hình VS môi trường Code <br>&emsp; + Tạo cụm ECS, Appilcation và configure API Gateway Load Balancer <br>&emsp; + Tạo Lambda function, API Gateway, S3 <br>&emsp; + Triển khai Stack và tải tập tin lên S3 <br>&emsp; + Tạo các Nested Stack với CDk và triển khai <br>&emsp; + Dọn dẹp tài nguyên. | 14/08/2025   | 15/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Thực hành**: Session Manager: <br> &emsp; + Tạo EC2 instance private, public và IAM Role <br> &emsp; + Kết nối đến máy chủ Public <br> &emsp; + Tạo kết nối đến máy chủ EC2 Private <br> &emsp; + Cập nhật IAM Role để truy cập vào S3 + Tạo S3 Buckets và S3 Gateway endpoint <br> &emsp; + Theo dõi session logs với SSM Session Manager <br> &emsp; + Cấu hình Port Forwarding <br> &emsp; + Dọn dẹp tài nguyên. | 13/08/2025   | 13/08/2025      | <https://cloudjourney.awsstudygroup.com/> |




### Kết quả đạt được tuần 8:

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


