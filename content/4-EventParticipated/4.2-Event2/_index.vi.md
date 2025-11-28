---
title: "Event 2"
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Bài thu hoạch “Generative AI with Amazon Bedrock”

### Mục Đích Của Sự Kiện

- Cung cấp kiến thức nền tảng về Generative AI và sự khác biệt so với Machine Learning truyền thống.
- Mô tả chi tiết về dịch vụ Amazon Bedrock và các mô hình nền tảng (Foundation Models).
- Hướng dẫn kỹ thuật về RAG (Retrieval Augmented Generation) để xây dựng ứng dụng AI thông minh, chính xác và tránh ảo giác.
- Giới thiệu hệ sinh thái các dịch vụ AI chuyên biệt của AWS.
### Danh Sách Diễn Giả

- **Lam Tuan Kiet** - Sr DevOps Engineer, FPT Software.
- **Danh Hoang Hieu Nghi** - AI Engineer, Renova Cloud.
- **Dinh Le Hoang Anh** - Cloud Engineer Trainee, First Cloud AI Journey.


### Nội Dung Nổi Bật

#### Sự chuyển dịch: Traditional ML vs Foudation Models

- **Traditional ML Models**: Chuyên biệt cho từng tác vụ cụ thể (Specific tasks), cần dữ liệu được gán nhãn (Labeled data), quy trình Train/Deploy phức tạp cho từng mục đích.
- **Foundation Models (FM)**: Được huấn luyện trên dữ liệu phi cấu trúc khổng lồ (Unlabeled data), có khả năng thích ứng cho nhiều tác vụ khác nhau như: Text generation, Summarization, Q&A, Chatbot.

#### Hệ sinh thái AI trên AWS

- **Amazon Bedrock**: Nơi hội tụ các mô hình FM hàng đầu từ các đối tác của AWS(AI21 Labs, Anthropic, Cohere, Meta, Stability AI,...) và mô hình của Amazon.
- **AWS Specialized AI Services**: Các dịch vụ AI của AWS có thể gọi là "mì ăn liền" được tối ưu cho tác vụ cụ thể mà không cần train mô hình:
    - Amazon Rekognition: Phát hiện đối tượng, Nhận diện khuôn mặt, Nhận diện cảm xúc, Nhận diện cảm xúc, Nhận diện người nổi tiếng, phân tích video - 0.001$/ảnh với 1 triệu ảnh đầu tiên
    - Amazon translate: Dịch thuật văn bản đa ngôn ngữ theo thời gian thực với độ chính xác cao và văn phong tự nhiên.
    - Amazon Textract: Trích xuất thông tin có cấu trúc (bảng biểu, form mẫu) từ văn bản quét hoặc PDF.
    - Amazon Transcribe: Chuyển đổi giọng nói thành văn bản
    - Amazon Polly: Chuyển đổi văn bản thành giọng nói.
    - Amazon Comprehend: Phân tích cảm xúc văn bản, trích xuất từ khóa và phân loại chủ đề tự động.
    - Amazon Kendra: Cho phép hỏi đáp bằng ngôn ngữ tự nhiên để tìm thông tin trong tài liệu nội bộ của doanh nghiệp.
    - Amazon Lookout: Phát hiện các bất thường trong dây chuyền sản xuất hoặc máy móc công nghiệp để bảo trì dự đoán.
    - Amazon Personalize: Xây dựng hệ thống gợi ý theo thời gian thực, sử dụng công nghệ máy học.

#### Kỹ thuật Prompting: Chain of Thought (CoT)

- So sánh giữa **Standard Prompting** là hỏi thẳng kết quả và **Chain-of-Thought Prompting**.
- CoT hướng dẫn mô hình suy luận từng bước để giải quyết các bài toán logic phức tạp, giúp tăng độ chính xác đáng kể so với việc chỉ đưa ra đáp án cuối cùng.

#### RAG (Retrieval Augmented Generation) – Trọng tâm kỹ thuật

- **Vấn đề**: Giải quyết hiện tượng "ảo giác" và thiếu kiến thức cập nhật của LLM.
- **Giải pháp**: Kết hợp khả năng truy xuất dữ liệu (Retrieval) từ Knowledge Base bên ngoài với khả năng tạo sinh (Generation) của LLM.
- **Quy trình Data Ingestion (Nạp dữ liệu)**:
    1. Dữ liệu thô (New data) $\rightarrow$ Chia nhỏ (Chunking).
    2. Đi qua Embeddings model (ví dụ: Amazon Titan Text Embeddings V2.0).
    3. Lưu trữ dưới dạng vector vào Vector Store (OpenSearch Serverless, Pinecone, Redis...).
- **RetrieveAndGenerate API**: API quản lý toàn bộ quy trình từ nhận input người dùng $\rightarrow$ tạo query embedding $\rightarrow$ truy xuất dữ liệu $\rightarrow$ bổ sung ngữ cảnh (augment prompt) $\rightarrow$ sinh câu trả lời.

### Những Gì Học Được

#### Về Tư Duy AI và Cloud

- Hiểu rõ khi nào nên dùng **Specialized AI Services** cho bài toán nhanh, cụ thể và khi nào dùng **Bedrock/GenAI** cho bài toán sáng tạo, phức tạp.
- Nắm vững tư duy thiết kế hệ thống RAG: Không chỉ là gọi API của LLM, mà là bài toán quản lý dữ liệu và vector hóa để cung cấp ngữ cảnh đúng cho AI tạo phản hồi chuẩn hơn.

#### Về Kiến Trúc Kỹ Thuật

- Kỹ thuật **Chain of Thought** là chìa khóa để tối ưu hóa kết quả đầu ra của mô hình mà không cần fine-tuning.
- Hiểu sâu về vai trò của Amazon Titan Embeddings V2.0 trong việc chuyển đổi văn bản đa ngôn ngữ thành vector (hỗ trợ 100+ ngôn ngữ, vector size linh hoạt 256/512/1024).

### Ứng Dụng Vào Công Việc
- Áp dụng Amazon Berock cho dự án hiện tại: Amazon Rekognition: nhận diện món ăn từ ảnh để tự động điền thông tin calo, Amazon Comprehend: phân tích text để chuẩn hóa món ăn lấy và ghi dữ liệu calo. 
- Áp dụng thử kĩ thuật RAG cho dự án hiện tại.
- Sử dụng Bedrock Agents để điều phối các tác vụ như truy vấn món ăn từ vector store, tính toán mục tiêu calo và xây dựng thực đơn từng ngày.

### Trải nghiệm trong Sự Kiện
Tham gia buổi workshop Generative AI with Amazon Bedrock mang lại cái nhìn rất thực tế về cách xây dựng ứng dụng AI hiện đại, đi từ lý thuyết nền tảng đến triển khai thực tế.

#### Kiến thức thực chiến từ chuyên gia
- Các diễn giả đã giải thích khá rõ ràng luồng đi của dữ liệu trong một hệ thống **RAG**, giúp tôi hình dung được "hộp đen" phía sau các ứng dụng Chatbot hiện nay đang sử dụng.
- Việc phân tích rõ ràng giữa **Traditional ML** và **Generative AI** giúp tôi định hình lại chiến lược chọn công nghệ cho các dự án sắp tới.

#### Trải nghiệm công nghệ
- Ấn tượng với **RetrieveAndGenerate API** của Bedrock vì nó giúp giảm bớt rất nhiều công sức code thủ công cho phần kết nối giữa Vector Store và LLM.
- Thấy được sức mạnh của **Amazon Titan Embedding** trong việc hỗ trợ đa ngôn ngữ, rất phù hợp cho các ứng dụng tại thị trường Việt Nam.

#### Bài học rút ra
- RAG là tiêu chuẩn mới: Để AI ứng dụng được trong doanh nghiệp, RAG là bắt buộc để đảm bảo tính chính xác và bảo mật dữ liệu.
- Hệ sinh thái toàn diện: AWS cung cấp đầy đủ từ tầng hạ tầng (Vector Store) đến tầng mô hình (Bedrock) và tầng ứng dụng (Agents), giúp việc triển khai nhanh chóng hơn rất nhiều.

#### Một Số Hình Ảnh Khi Tham Gia Sự Kiện

![Anh](/images/2-Proposal/genaigenai.png)
![Anh](/images/2-Proposal/genai1.png)
![Anh](/images/2-Proposal/genai2.png)
![Anh](/images/2-Proposal/genai3.png)

> Tổng thể, sự kiện không chỉ cung cấp kiến thức kỹ thuật mà còn giúp tôi thay đổi cách tư duy về thiết kế ứng dụng, hiện đại hóa hệ thống và phối hợp hiệu quả hơn giữa các team.
