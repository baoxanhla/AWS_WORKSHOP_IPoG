---
title: "Worklog Tuần 9"
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9:

* Làm quen với hệ sinh thái dữ liệu và Machine Learning trên AWS.
* Nắm được các tính năng chính trong hệ sinh AI của AWS hỗ trợ.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tìm hiểu AWS Glue <br>&emsp; + Crawler <br> - Tìm hiểu Amazon Athena <br> - Tìm hiểu Amazon QuickSight <br> - Tìm hiểu Amazon SageMaker | 03/11/2025   | 03/11/2025   | <https://cloudjourney.awsstudygroup.com/>   |
| 3   | - **Thực hành**: Phân tích dữ liệu: <br>&emsp; + Tạo IAM Role và IAM policy + Tạo S3 Bucket <br>&emsp; + Tạo Glue Crawler và kiểm tra dữ liệu <br>&emsp; + Tạo notebook với AWS Glue Studio <br>&emsp; + Phân tích với Athena và trực quan với QuickSight <br>&emsp; Dọn dẹp tài nguyên | 04/11/2025   | 04/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - **Thực hành**: Phân tích dữ liệu với Amazon SageMaker: <br>&emsp; + Tạo SageMaker Studio <br>&emsp; + Chuẩn bị dataset, phân tích dữ liệu và export dữ liệu tới S3 <br>&emsp; + Train và tinh chỉnh mô hình Machine learning <br>&emsp; +  Triển khai và đánh giá hiệu suất mô hình <br>&emsp; + tinh chỉnh mô hình tự động <br>&emsp; + Dọn dẹp tài nguyên | 05/11/2025   | 05/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Tìm hiểu các Amazon Bedrock  <br>&emsp; + Các Foundation model <br>&emsp; + Bedrock Agents <br>&emsp; + Knowledge Bases <br>&emsp; + Bedrock Inference Features| 06/11/2025   | 06/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Tìm hiểu các tính năng trong Pre-trained AI Services <br>&emsp; + Amazon Rekognition <br>&emsp; + Amazon translate <br>&emsp; + Amazon Textract <br>&emsp; + Amazon Transcribe <br>&emsp; + Amazon Polly <br>&emsp; + Amazon Comprehend <br>&emsp; + Amazon Kendra <br>&emsp; + Amazon Lookout <br>&emsp; + Amazon Personalize | 07/11/2025   | 07/11/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 9:

* Hiểu và biết cách xây dựng luồng xử lý dữ liệu Serverless:

  * Hiểu rmô hình Data Lake hiện đại trên AWS, Lấy S3 làm trung tâm lưu trữ 
  * AWS Glue: Glue Crawler trong việc tự động phát hiện schema từ dữ liệu thô (CSV/JSON trong S3) và tạo Metadata 
  * Table trong Glue Data Catalog, biến dữ liệu phi cấu trúc thành có cấu trúc để query.
  * Amazon Athena: Thực hiện được truy vấn SQL trực tiếp trên dữ liệu nằm tại S3 mà không cần provision server hay load dữ liệu vào database truyền thống.
  * Amazon QuickSight: Biết cách kết nối với Athena để trực quan hóa dữ liệu, tạo dashboard BI (Business Intelligence) để ra quyết định dựa trên dữ liệu.

* Hiểu quy trình phát triển Machine Learning trên Amazon SageMaker:

  * Môi trường: SageMaker Studio
  * Training: Hiểu cơ chế tách biệt tài nguyên: Notebook dùng để code, nhưng khi gọi fit(), SageMaker sẽ khởi tạo cụ
  * Training Cluster riêng biệt, train xong tự tắt để tối ưu chi phí.
  * Optimization: Biết cách sử dụng Automatic Model Tuning để tìm ra bộ tham số tốt nhất cho mô hình thay vì thử thủ công.
  * Deployment: Triển khai mô hình đã train thành một Endpoint (REST API) để phục vụ dự đoán theo thời gian thực.
* Nắm bắt xu hướng Generative AI với Amazon Bedrock:

* Hiểu được sự dịch chuyển từ việc "tự train model" sang việc "sử dụng Foundation Models (FM)" qua API .
  * Nắm được các thành phần cốt lõi để xây dựng ứng dụng LLM hiện đại:
    * Knowledge Bases: Cơ chế RAG (Retrieval-Augmented Generation) để cung cấp dữ liệu riêng của doanh nghiệp cho AI.
    * Agents: Giúp AI không chỉ "chat" mà còn thực hiện hành động (gọi API, tra cứu dữ liệu).

* Nắm được hệ sinh thái Pre-trained AI Services (AI không cần code):

  * Phân loại được các nhóm dịch vụ để áp dụng đúng bài toán mà không cần build model từ đầu:

    * Vision: Rekognition (nhận diện ảnh/video).
    * Speech/Audio: Transcribe (STT), Polly (TTS).
    * NLP/Text: Translate, Comprehend (phân tích cảm xúc/entity), Textract (OCR tài liệu).
    * Specialized: Personalize (gợi ý), Lookout (bảo trì dự đoán).
