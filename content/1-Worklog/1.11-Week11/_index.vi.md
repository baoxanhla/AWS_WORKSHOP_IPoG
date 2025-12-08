---
title: "Worklog Tuần 11"
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần 11:

* Hiểu quy trình CI/CD và bộ công cụ AWS Code Series.
* Trải nghiệm được các dịch vụ Amazon AI

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tìm hiểu các dịch vụ orchestrator CI/CD trên AWS <br>&emsp; + AWS CodeCommit <br>&emsp; + AWS CodeBuild <br>&emsp; + AWS CodeDeploy <br>&emsp; + AWS CodePipeline | 17/11/2025   | 17/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Tìm hiểu về AWS Elastic Beanstalk <br>&emsp; + Application <br>&emsp; + Enviroment <br> - **Thực hành:** Triển khai ứng dụng wed chạy trên AWS với Elastic Beanstalk  <br>&emsp; + Tạo CloudFormation stack <br>&emsp; + Kết nối EC2 linux instance và cài đặt database <br>&emsp; + Kiểm tra máy chủ local để tải project <br>&emsp; + Triển khai trên ElasticBeanstalk <br>&emsp; + Cập nhật ứng dụng <br>&emsp; + Kiểm tra môi trường và truy vấn thông tin máy chủ EC2 <br>&emsp; + Dọn dẹp tài nguyên.| 18/11/2025   | 18/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Cập nhật lại được các kiến thức về các Amazon Bedrock <br> - Tìm hiểu rõ hơn về các dịch vụ pre-train AI service cũng như chi phí và cách sử dụng API | 19/11/2025   | 19/11/2025  | <https://cloudjourney.awsstudygroup.com/>  |
| 5   | - **Thực hành**: Sử dụng Amazon Polly <br>&emsp; + Cài đặt DynamoDB  <br>&emsp; + Khám phá Amazon Polly <br>&emsp; + Tạo Speech và speech marks bằng AWS CLI <br>&emsp; + Tạo speech marks bằng AWS polly SDK dành cho java  | 20/11/2025   | 20/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Thực hành:** Sử dụng Amazon Rekognition <br>&emsp; + Tạo Cognito Identity Pool <br>&emsp; + Phát hiện đối tượng bằng Amazon Rekonition <br>&emsp; + Nhận diện khuôn mặt <br>&emsp; + Thử nghiệm ứng dụng tìm người <br>&emsp; + Gắn EBS volume                                                                                         | 21/11/2025   | 21/11/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 11:

* Hiểu quy trình "Software Supply Chain" trên AWS (CI/CD):

* Hiểu rõ sự chuyển dịch từ việc deploy thủ công (copy file, SSH vào server) sang quy trình tự động hóa hoàn toàn với bộ AWS Code Series.
* Nắm rõ vai trò của từng dịch vụ:

    * AWS CodeCommit: Quản lý phiên bản mã nguồn (Git-based), nơi khởi nguồn của mọi thay đổi.
    * AWS CodeBuild: Môi trường biên dịch và kiểm thử tự động (Unit Test), đảm bảo code "sạch" trước khi đi tiếp.
    * AWS CodeDeploy: Tự động hóa việc đẩy code lên các đội hình server, giảm thiểu downtime và lỗi con người.
    * AWS CodePipeline: "Nhạc trưởng" điều phối toàn bộ quy trình trên thành một dòng chảy liên tục.

* Nắm được platform as a Service với Elastic Beanstalk:

  * Hiểu được giá trị của việc thay vì phải tự cấu hình VPC, EC2, Load Balancer, Auto Scaling Group thủ công thì biết dùng Elastic Beanstalk để lo trọn bộ quá trình của việc này.


* Cập nhật tầm nhìn chiến lược về Generative AI Qua sự kiện:  Generative AI with Amazon Bedrock

  * Hiểu sự chuyển dịch mô hình từ "Tự training model" sang "Sử dụng Foundation Models (FMs) qua API".
  * Nắm bắt được các khái niệm cốt lõi của Amazon Bedrock: Serverless AI, khả năng tích hợp Knowledge Base (RAG) và Agents để xây dựng ứng dụng AI doanh nghiệp bảo mật và riêng tư.

* Thực hành chuyên sâu tích hợp AI Services:
  * Với Amazon Polly: Chuyển đổi văn bản thành âm thanh
    * Biết chuyển đổi văn bản thành giọng nói đơn giản
    * Biết xử lý Speech Marks (Metadata về thời gian thực của từ ngữ), một kỹ thuật tạo nhép giọng nói cho nhân vật ảo
    * Biết cách sử dụng SDK (Java) để tích hợp Polly vào backend
  * Với Amazon Rekognition:
    * biết dùng Cognito Identity Pool để cấp quyền tạm thời cho ứng dụng truy cập trực tiếp vào Rekognition mà không cần hard-code Access Key
    * Hiểu cách sử dụng API để giải quyết các bài toán thị giác máy tính phức tạp: Nhận diện khuôn mặt, phát hiện vật thể  và định danh người.

