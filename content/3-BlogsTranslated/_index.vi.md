---
title: "Các bài blogs đã dịch"
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

Trong quá trình tìm hiểu và học về các dịch vụ của AWS tôi cũng dịch qua các bài Blog để nâng cao kiến thức: 

###  [Blog 1 - How a Customer Reduced Total Cost of Ownership (TCO) by 28% for Storage with Amazon FSx for NetApp ONTAP](3.1-Blog1/)
Blog này trình bày cách một tổ chức đa chi nhánh tối ưu hóa lưu trữ bằng Amazon FSx for NetApp ONTAP. Kiến trúc sử dụng FlexCache, SnapMirror và Multi-AZ giúp cải thiện hiệu năng truy cập, đơn giản hóa vận hành và **giảm 28% tổng chi phí sở hữu (TCO)** so với on‑premises.

###  [Blog 2 - Automating vector embedding generation in  Aurora PostgreSQL with  Bedrock](3.2-Blog2/)
Blog này hướng dẫn cách tự động sinh vector embeddings cho dữ liệu PostgreSQL sử dụng **Aurora + pgvector + Bedrock**. Bài viết trình bày nhiều chiến lược (triggers, Lambda đồng bộ/bất đồng bộ, SQS batch, pg_cron), phân tích ưu nhược điểm về **độ trễ, tính đồng bộ, khả năng mở rộng** và hướng dẫn thiết kế pipeline embedding tối ưu cho ứng dụng AI.

###  [Blog 3 - Group database tables under AWS Database Migration Service tasks for PostgreSQL source engine](3.3-Blog3/)
Blog này giải thích cách phân tích metadata PostgreSQL và đặc tính bảng để nhóm bảng hợp lý vào các AWS DMS task. Hướng dẫn giúp **cân bằng tải, giảm độ trễ CDC**, xử lý bảng lớn, bảng LOB hoặc thiếu PK/UK, và đưa ra best practice để migration dữ liệu quy mô lớn hiệu quả.
