---
title: "Worklog Tuần 7"
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:

* Nắm được kiến trúc và cách hoạt động của mô hình Serverless với Lambda và API Gateway.
* Hiểu được cơ chế vận hành của AWS Lambda và hiểu cơ bản về kiến trúc Event-Driven
* Biết cách sử dụng sử dụng SQS và SNS với kiến trúc hợp lí 
+ Cấu hình API Gateway trigger Lambda


  + Lưu dữ liệu từ Lambda xuống DynamoDB
### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tìm hiểu về AWS Lambda <br>&emsp; + IAM Role cho Lambda <br>&emsp; + Lambda function <br> - Tìm hiểu về Amazon API Gateway <br>&emsp; + Các method <br>&emsp; + CORS <br> - **Thực hành**: <br>&emsp; + Tạo role cấp quyền tối thiểu cho Lambda để truy cập S3 và  DynamoDB <br>&emsp; + Tạo Lambda function để xử lí file upload <br>&emsp; + Cấu hình API Gateway trigger Lambda <br>&emsp; + Lưu dữ liệu từ Lambda xuống DynamoDB | 11/08/2025   | 11/08/2025      |
| 3   | - **Thực hành**: Tương tác giữa Lambda với S3 và DynamoDB <br>&emsp; + Tạo lambda function xử lý ảnh <br>&emsp; + Tạo S3 Bucket <br>&emsp; + Tạo IAM Policy cho lambda fuction và kiểm tra hoạt động <br>&emsp; + Tạo và quản lý bảng trong AWS DynamoDB + Tạo lambda fuction để gi dữ liệu vào <br>&emsp; + Dọn dẹp tài nguyên  | 12/08/2025   | 12/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - **Thực hành**: Host wed tỉnh với S3 <br>&emsp; + Tạo Bucket, bật enable, gán policy và tải thư mục frontend lên S3 <br>&emsp; + Tạo bảng DynamoDB, triển khai lambda function để ghi, đọc và xóa dữ liệu <br>&emsp; + Thiết lập API Geteway <br>&emsp; + Kiểm trai API với Postman <br>&emsp; + Kiểm tra API với front-end <br>&emsp; + Dọn dẹp tài nguyên| 14/08/2025   | 15/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Tìm hiểu kiến trúc Event-driven với Amazon SQS và SNS <br>&emsp; + SQS: Pub và Sub <br>&emsp; + SNS: Queue <br> - **Thực hành**: <br>&emsp; + Tạo Queue và chủ đề SNS <br>&emsp; + Tạo API và Lambda function để tương tác với Queue và chủ đề SNS <br>&emsp; + Kiểm tra hoạt động với APIs <br>&emsp; + Dọn dẹp tài nguyên | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Tìm hiểu AWS Step Functions <br>&emsp; + Orchestrate microservices  | 15/08/2025   | 15/08/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 7:

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


