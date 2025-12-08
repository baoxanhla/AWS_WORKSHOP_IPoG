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
+ Cấu hình API Gateway làm trigger Lambda


  + Lưu dữ liệu từ Lambda xuống DynamoDB
### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tìm hiểu về AWS Lambda <br>&emsp; + IAM Role cho Lambda <br>&emsp; + Lambda function <br> - Tìm hiểu về Amazon API Gateway <br>&emsp; + Các method <br>&emsp; + CORS <br> - **Thực hành**: <br>&emsp; + Tạo role cấp quyền tối thiểu cho Lambda để truy cập S3 và  DynamoDB <br>&emsp; + Tạo Lambda function để xử lí file upload <br>&emsp; + Cấu hình API Gateway trigger Lambda <br>&emsp; + Lưu dữ liệu từ Lambda xuống DynamoDB | 20/10/2025   | 20/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - **Thực hành**: Tương tác giữa Lambda với S3 và DynamoDB <br>&emsp; + Tạo lambda function xử lý ảnh <br>&emsp; + Tạo S3 Bucket <br>&emsp; + Tạo IAM Policy cho lambda fuction và kiểm tra hoạt động <br>&emsp; + Tạo và quản lý bảng trong AWS DynamoDB + Tạo lambda fuction để ghi dữ liệu vào <br>&emsp; + Dọn dẹp tài nguyên  | 21/10/2025   | 21/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - **Thực hành**: Host website tĩnh trên S3 <br>&emsp; + Tạo Bucket, bật enable, gán policy và tải thư mục frontend lên S3 <br>&emsp; + Tạo bảng DynamoDB, triển khai lambda function để ghi, đọc và xóa dữ liệu <br>&emsp; + Thiết lập API Geteway <br>&emsp; + Kiểm trai API với Postman <br>&emsp; + Kiểm tra API với front-end <br>&emsp; + Dọn dẹp tài nguyên| 22/10/2025   | 22/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Tìm hiểu kiến trúc Event-driven với Amazon SQS và SNS <br>&emsp; + SQS: queue<br>&emsp; + SNS: Pub và Sub  <br> - **Thực hành**: <br>&emsp; + Tạo Queue và chủ đề SNS <br>&emsp; + Tạo API và Lambda function để tương tác với Queue và chủ đề SNS <br>&emsp; + Kiểm tra hoạt động với APIs <br>&emsp; + Dọn dẹp tài nguyên |23/10/2025   | 23/10/2025| <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Tìm hiểu AWS Step Functions <br>&emsp; + Orchestrate microservices  | 24/10/2025   | 24/10/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 7:

* Hiểu biết về Kiến trúc Serverless trên AWS
  * Nắm được kiến trúc và mô hình hoạt động của AWS Lambda, vòng đời thực thi và chi phí dựa trên thời gian chạy.
  * Hiểu rõ API Gateway hoạt động như một HTTP front-door cho Lambda, bao gồm:
    * REST API, HTTP API: Các loại API trong API Gateway dùng để expose backend; REST API đầy đủ tính năng, HTTP API nhẹ và tối ưu chi phí.
    * Methods: Định nghĩa hành động HTTP (GET/POST/PUT/DELETE) và liên kết đến Lambda hoặc backend khác.
    * CORS: Cho phép front-end từ domain khác gọi API, cấu hình qua các header CORS.
    * Integration request/response: Lớp chuyển đổi dữ liệu giữa API Gateway và backend, gồm mapping input và output.

  * Hiểu cách thiết kế kiến trúc event-driven, luồng dữ liệu và ưu điểm so với mô hình truyền thống.
* Triển khai được Lambda – API Gateway – DynamoDB – S3
  * Tạo IAM Role với quyền tối thiểu (Least Privilege) cho Lambda truy cập S3 và DynamoDB.
  * Tạo Lambda Function để:
    * Xử lý file upload từ S3
    * Ghi, đọc, cập nhật dữ liệu DynamoDB
  * Tạo API Gateway để trigger Lambda và xử lý request/response.
  * Cấu hình static website hosting trên S3 và kết nối front-end với API Gateway.

* Tương tác giữa Lambda – S3 – DynamoDB

* Tạo S3 bucket và bật event notifications cho Lambda.
  * Viết Lambda xử lý ảnh hoặc dữ liệu upload vào S3.
  * Thao tác CRUD với DynamoDB từ Lambda.
  * Tạo bảng DynamoDB, index (nếu cần) và xử lý dữ liệu nhiều dạng.

* Hiểu và triển khai hệ thống Event-driven với SNS & SQS

  * Nắm được mô hình:
    * SNS (Publisher → Topic → Subscriber)
    * SQS (Producer → Queue → Consumer)
  * Tạo SNS topic và SQS queue, kết nối SNS → SQS (fan-out).
  * Viết Lambda function để publish và consume message.
  * Test luồng truyền thông qua API Gateway và Lambda.

* Tìm hiểu AWS Step Functions
  * Hiểu khái niệm orchestration so với choreography.
  * Biết cách Step Functions điều phối nhiều Lambda/microservices qua State Machine.
