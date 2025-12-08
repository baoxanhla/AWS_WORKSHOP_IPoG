---
title: "Worklog Tuần 12"
weight: 2
chapter: false
pre: " <b> 1.12 </b> "
---

### Mục tiêu tuần 12:

* Ôn tập hệ thống kiến thức serverless và AI 
* Thiết kế chi tiết bảng database DynamoDB cho dự án và API
* Kiểm tra chi tiết về kết nối giữa các dịch vụ trong dự án

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Ôn tập và thiết kế database (DynamoDB) <br>&emsp; + Xem lại kiến thức về Partition Key (PK) và Sort Key (SK) <br> - **Thực hành** <br>&emsp; + Thiết kế Schema cho các bảng của dự án <br>&emsp; + Xác định các Access Pattern (Cách truy vấn dữ liệu) cho dự án.   | 24/11/2025   | 24/11/2025    | <https://cloudjourney.awsstudygroup.com/>  |
| 3   | - Ôn tập và thiết kế API (API Gateway + Lambda): <br> &emsp; + Xem lại cách tạo REST API, Lambda Proxy Integration. <br> &emsp; + Liệt kê danh sách API endpoint cần thiết: POST, GET | 25/11/2025   | 25/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Ôn tập luồng tích hợp AI với Bedrock <br> &emsp; + Xem lại các cách gọi API Bedrock <br> &emsp; + Xem lại các Prompt Engineering cơ bản| 26/11/2025   | 26/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Ôn tập bào mật và xác thực (Cognito + IAM ) <br> &emsp; + Xem lại luồng xác thực User Login -> Nhận Token -> Gửi Token lên API Gateway. <br> &emsp; + Xem lại IAM Policy về cách cấp quyền tối thiểu  | 27/11/2025   | 27/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Ôn lại các cách giám sát hệ thống và vận hành <br> &emsp; + Xem lại CloudWatch để lên kế hoạch giám sát khi dự án chạy. <br> &emsp; + Xem lại Boto3 <br> &emsp; + Lập kế hoạch các bước triển khai dự án | 28/11/2025   | 28/11/2025 | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 12:

* Hoàn thiện Schema Design cho DynamoDB:
  * Thiết kế bảng dữ liệu cụ thể, tối ưu cho việc truy xuất dữ liệu

* Xác định rõ ràng giao diện kết nối:
  * Định nghĩa rõ input/output cho các hàm Lambda. 

  * Nắm cách dùng thư viện boto3 để kết nối các "mảnh ghép" AWS lại với nhau.

* Chuẩn bị sẵn sàng kịch bản cho AI (Prompt Strategy) để test Bedrock đúng như mong đợi

* Hiểu rõ luồng đi của Identity (Danh tính) từ Cognito qua API Gateway xuống Lambda.
