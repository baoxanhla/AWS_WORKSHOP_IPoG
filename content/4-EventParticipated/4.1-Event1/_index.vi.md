---
title: "Event 1"
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Bài thu hoạch “Cloud Day”

### Mục Đích Của Sự Kiện

- Giới thiệu xu hướng phát triển của AI tại Việt Nam và cơ hội kinh tế.
- Trình bày sự tiến hóa từ Generative AI đến Agentic AI.
- Giới thiệu các giải pháp của AWS như **Amazon Bedrock**, **AgentCore**, và **SageMaker Unified Studio** trong việc xây dựng, triển khai và vận hành AI agent.

### Danh Sách Diễn Giả

- **Kien Nguyen** - Solutions Architect
- **Jun Kai Loke** - AI/ML Specialist SA, AWS
- **Tamelly Lim** - Storage Specialist SA, AWS
- **Binh Tran** - Senior Solutions Architect, AWS
- **Taiki Dang** - Solutions Architect, AWS
- **Michael Armentano** - Principal WW GTM Specialist, AWS

### Nội Dung Nổi Bật

#### Tác động của AI đến kinh tế Việt Nam

- AI có thể đóng góp **120–130 tỷ USD vào GDP** Việt Nam vào năm 2040 (~25%).
- Thị trường AI trị giá **750 triệu USD**, tăng trưởng **15–18%/năm**.
- Việt Nam hiện có **765 startup AI**, đứng **thứ 2 ASEAN**.
- Cơ hội lớn nhưng vẫn ở **giai đoạn đầu**, cần thêm hạ tầng, nhân tài và chính sách.

#### Sự tiến hóa của AI → Agentic AI

- **Generative AI Assistants** → **Generative AI Agents** → **Agentic AI Systems**.
- Các hệ thống AI ngày càng ít phụ thuộc con người:
- Multi-agent systems: các agent phối hợp cùng nhau giải quyết tác vụ phức tạp.
- Mức độ tự động hóa tăng dần, **giảm dần sự giám sát của con người**:

#### Ứng dụng của Agentic AI trong tổ chức

- Nâng cao **năng suất làm việc**, **tự động hóa quy trình**, thúc đẩy **đổi mới và nghiên cứu**.
- Dự đoán đến **2028**, **33% ứng dụng doanh nghiệp** sẽ tích hợp Agentic AI.
- **15% quyết định thường ngày** trong doanh nghiệp sẽ được đưa ra tự động nhờ Agentic AI.

#### Amazon Bedrock – Nền tảng AI toàn diện

- Cung cấp đa dạng mô hình từ nhiều hãng hàng đầu.
- Cho phép tùy chỉnh mô hình với dữ liệu riêng, đảm bảo bảo mật và kiểm soát chi phí.
- Tích hợp Responsible AI checks để đảm bảo an toàn.
- Hỗ trợ triển khai và vận hành agent nhanh chóng, an toàn và mở rộng dễ dàng.

#### Amazon Bedrock AgentCore

- Môi trường **triển khai và vận hành Agent** bảo mật, có khả năng mở rộng cao.
- Hỗ trợ các framework: **LangChain, CrewAI, LangGraph, Strands Agents**.
- Quản lý **short-term và long-term memory**, có **truy xuất ngữ nghĩa (semantic search)**.
- **Tích hợp và khám phá tool** dễ dàng.

#### Hạ tầng dữ liệu và AI

- Giới thiệu **Amazon SageMaker Unified Studio** – trung tâm hợp nhất dữ liệu, phân tích và AI.
- Kết nối chặt chẽ với:
  - **Amazon Redshift, Athena, EMR, Glue** – xử lý và lưu trữ dữ liệu.
  - **Amazon QuickSight** – trực quan hóa dữ liệu.
  - **Amazon Bedrock** – phát triển ứng dụng GenAI.
- Hỗ trợ tích hợp Zero-ETL giữa **S3 data lake** và **Redshift data warehouse**.

#### Data Lakehouse

- Hỗ trợ nhiều loại lưu trữ: **S3 Tables, Redshift Managed Storage**.
- Kết nối các nguồn dữ liệu lớn: **Aurora, DynamoDB, MSK, Kinesis, OpenSearch, Salesforce, SAP, Facebook Ads**.

### Những Gì Học Được

#### Về Tư Duy AI và Cloud

- Hiểu được xu hướng **Agentic AI** là giai đoạn tiếp theo của Generative AI và đang hot hiện tại.
- Agentic AI không chỉ là Chatbot mà là hệ thống có thể hành động và tự ra quyết định.
- Nắm bắt cách **AWS Bedrock** cung cấp nền tảng cho doanh nghiệp xây dựng hệ thống AI thông minh.
- Thấy rõ tầm quan trọng của **AI agents** trong tự động hóa doanh nghiệp và sáng tạo.

#### Về Kiến Trúc Kỹ Thuật

- Hiểu mối liên kết giữa **Bedrock – SageMaker – Redshift – S3** trong một hệ sinh thái AI hoàn chỉnh.
- Nắm được cách AWS xử lý **memory, tool discovery, và observability** cho AI agent.

### Ứng Dụng Vào Công Việc
- Áp dụng Amazon Berock cho dự án hiện tại: Sử dụng Amazon Titan Embeddings để tạo embedding 
- Thử nghiệm Zero-ETL với Amazon Redshift để đơn giản hóa pipeline dữ liệu từ Aurora/DynamoDB.
- Đánh giá việc sử dụng Amazon Bedrock AgentCore để xây dựng các tác tử AI tự động hóa quy trình nghiệp vụ (thay vì chỉ dùng Lambda + Bedrock cơ bản).


### Trải nghiệm trong Sự Kiện
Tham gia sự kiện **Cloud Day** là một trải nghiệm rất bổ ích, giúp tôi có cái nhìn rõ ràng hơn về cách các doanh nghiệp đang ứng dụng AI để hiện đại hóa hệ thống và nâng cao năng suất.

#### Học hỏi từ các diễn giả có chuyên môn cao
- Các diễn giả đến từ **AWS** chia sẻ sâu về **Agentic AI** và sự khác biệt so với Generative AI truyền thống.
- Qua các ví dụ thực tế của Amazon, tôi hiểu rõ hơn cách họ triển khai **multi-agent systems** để tối ưu quy trình doanh nghiệp.

#### Trải nghiệm kỹ thuật thực tế
- Tìm hiểu cách hoạt động của **Amazon Bedrock AgentCore**, từ cách nó xử lý **short/long-term memory** đến quản lý công cụ tích hợp.
- Thấy rõ quy trình **kết nối dữ liệu từ S3 – Redshift – SageMaker**, và cách AI agents truy xuất dữ liệu để trả lời theo ngữ cảnh.
- Hiểu rõ mô hình **Lakehouse** và cơ chế **Zero-ETL integration** giữa data lake và data warehouse.

#### Ứng dụng công cụ hiện đại

- Học cách **triển khai Agentic AI** nhanh chóng trên **AWS Bedrock**, với độ bảo mật và khả năng mở rộng cao.

#### Bài học rút ra
- Agentic AI không chỉ là công nghệ mới, mà là bước tiến chiến lược để doanh nghiệp đạt **tự động hóa cấp hệ thống**.
- Hạ tầng AI hiện đại cần được **thiết kế dựa trên dữ liệu và cloud-native architecture**.
- AWS đang dẫn đầu trong việc cung cấp **nền tảng toàn diện cho AI/ML**, đặc biệt là Bedrock và SageMaker.
- Thấy rõ tầm quan trọng của **AI agents** trong tự động hóa doanh nghiệp và sáng tạo.

#### Một Số Hình Ảnh Khi Tham Gia Sự Kiện

![Image](/images/2-Proposal/clouday.png)
![Image](/images/2-Proposal/cloudday1.png)
![Image](/images/2-Proposal/cloudday2.png)
![Image](/images/2-Proposal/cloudday3.png)

> Tổng thể, sự kiện không chỉ cung cấp kiến thức kỹ thuật mà còn giúp tôi thay đổi cách tư duy về thiết kế ứng dụng, hiện đại hóa hệ thống và phối hợp hiệu quả hơn giữa các team.
