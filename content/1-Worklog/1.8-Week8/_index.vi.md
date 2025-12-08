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
| 2   |  - Tìm hiểu AWS CloudFormation, Cloud9 <br>&emsp; + Template: Json, Yaml <br>&emsp; + Stack <br>&emsp; + Drift Detection<br> -**Thực hành** <br>&emsp; + Sử dụng Cloud9 để tạo CloudFormation template cơ bản | 27/10/2025   | 27/10/2025   | <https://cloudjourney.awsstudygroup.com/>   |
| 3   | - **Thực hành:** CloudFormation nâng cao: <br>&emsp; + Tạo Lambda Funtion <br>&emsp; + Tạo Stack <br>&emsp; + Kết nối EC2 instance <br>&emsp; + Ánh xạ và StackSets <br>&emsp; + Drift Detection <br>&emsp; + Dọn dẹp tài nguyên   | 28/10/2025   | 28/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Tìm hiểu AWS Systems Manager (SSM) <br>&emsp; + Patch Manager <br>&emsp; + Run Command <br>&emsp; + Session manager <br> - **Thực hành** <br> &emsp; + Tạo EC2 instance, IAM Role và gán IAM Role <br> &emsp; + Cấu hình Patch Manager + Run Comman <br> &emsp; + Dọn dẹp tài nguyên   | 29/10/2025   | 29/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Tìm hiểu AWS CDK <br> **Thực hành**: AWS CDK với VS Code <br>&emsp; + Tạo EC2 instance public <br>&emsp; + Cấu hình môi trường VS Code để sử dụng AWS CDK <br>&emsp; + Tạo cụm ECS, Application và Kết hợp API Gateway với Application Load Balancer <br>&emsp; + Tạo Lambda function, API Gateway, S3 <br>&emsp; + Triển khai Stack và tải tập tin lên S3 <br>&emsp; + Tạo các Nested Stack với CDk và triển khai <br>&emsp; + Dọn dẹp tài nguyên. | 30/10/2025   | 30/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Thực hành**: Session Manager: <br> &emsp; + Tạo EC2 instance private, public và IAM Role <br> &emsp; + Kết nối đến máy chủ Public <br> &emsp; + Tạo kết nối đến máy chủ EC2 Private <br> &emsp; + Cập nhật IAM Role để truy cập vào S3 + Tạo S3 Buckets và S3 Gateway VPC Endpoint <br> &emsp; + Theo dõi session logs với SSM Session Manager <br> &emsp; + Cấu hình Port Forwarding <br> &emsp; + Dọn dẹp tài nguyên. | 31/10/2025   | 31/10/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 8:

* Hiểu thực hành được cơ bản về CloudFormation
  * Hiểu kiến trúc CloudFormation, cách template hoạt động và vòng đời của Stack.
  * Phân biệt được các thành phần chính:
    * Template : định nghĩa tài nguyên (YAML/JSON)
    * Parameters, Mappings, Resources, Outputs
    * Stack: một nhóm tài nguyên triển khai từ template
    * StackSets: triển khai stack cho nhiều tài khoản / nhiều region
    * Drift Detection: kiểm tra sự khác biệt giữa tài nguyên thực tế và template

  * Tạo được CloudFormation template cơ bản để triển khai tài nguyên (EC2, Lambda, Security Group…).

* Triển khai CloudFormation nâng cao

  * Tạo stack triển khai Lambda function và EC2.
  * Biết cách sử dụng Mappings, Parameters, Outputs trong template.
  * Sử dụng được StackSets để triển khai cho nhiều Region/AWS Account.
  * Thực hành Drift Detection để phát hiện thay đổi so với template.
  * Thực hành cơ bản được quy trình deploy – update – delete stack.

* Biết các sử dụng AWS Systems Manager (SSM)

  * Tạo EC2 và cấu hình IAM Role để kết nối với SSM.
  * Sử dụng Session Manager để kết nối EC2 mà không cần SSH/Keypair.
  * Thực hành:

    * Chạy lệnh từ xa với SSM Run Command
    * Cấu hình và chạy Patch Manager để cập nhật OS
    * Ghi logs truy cập EC2 vào S3
    * Thực hành Port Forwarding qua SSM

  * Hiểu lợi ích bảo mật khi không mở port 22.

* Biết cách dùng Session Manager

  * Kết nối EC2 Public → EC2 Private thông qua Session Manager.
  * Tạo và sử dụng S3 Gateway VPC Endpoint để EC2 private truy cập S3 mà không cần Internet.
  * Theo dõi hoạt động trong Session Manager Logs.
  * Dọn dẹp tài nguyên.