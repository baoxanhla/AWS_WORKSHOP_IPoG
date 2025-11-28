---
title: "Worklog Tuần 6"
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:

* Biết các dịch vụ lưu trữ dữ liệu quan hệ (SQL) và phi quan hệ (NoSQL) của AWS tùy vào nhu cầu lưu trữ
* Biết cách triển khai, vận hành và tối ưu hóa cơ sở dữ liệu trên AWS 
* Hiểu về AWS Catche để tăng tốc truy xuất dữ liệu

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tìm hiểu về Amazon RDS và Aurora <br>&emsp; + Các Engine: MySQL, PostgreSQL... <br>&emsp; + Tính khả dụng Multi-AZ <br>&emsp; + Hiệu năng Read Replicas <br>&emsp; + Backup và khôi phục tự động     | 11/08/2025   | 11/08/2025      |
| 3   | - **Thực hành**: <br>&emsp; + Chuẩn bị môi trường để instance RDS: Tạo VPC, EC2, RDS Security Group, DB Subnet Group <br>&emsp; + Tạo EC2 Instance <br>&emsp; + Tạo RDS Database Instance trong Private Subnet kết nối với EC2 <br>&emsp; + Triển khai ứng dụng <br>&emsp; + Backup và khôi phục tự động <br>&emsp; + Dọn dẹp tài nguyên  | 12/08/2025   | 12/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Tìm hiểu Amazon DynamoDB: NoSQL <br>&emsp; + Các thành phần cốt lõi <br>&emsp; + Primary key và Soft key <br>&emsp; + Read/Write Capacity với On-demand hoặc Provisioned <br> - **Thực hành**: Sử dụng AWS Console và Cloudshell để: <br>&emsp; + Tạo table <br>&emsp; + Ghi, đọc và cập nhật dữ liệu <br>&emsp; + Truy vấn dữ liệu <br>&emsp; + Tạo global secondary index <br>&emsp; + Truy vấn secondarry index| 13/08/2025   | 13/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Tìm hiểu các gói python của AWS ADK <br>&emsp; + Botocore <br>&emsp; + Boto3 <br> - **Thực hành**: <br>&emsp; + Cấu hình AWS CLI với thư viện Boto3 <br>&emsp; + Sử dụng Python để phát triển với DynamoDB: Tạo Table, ghi, đọc, cập nhật, xóa dữ liệu, Tải dữ liệu mẫu, Truy vấn, quét dữ liệu và xóa dữ liệu table <br>&emsp; + Dọn dẹp tài nguyên.  | 14/08/2025   | 15/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Tìm hiểu Amazon ElastiCache <br>&emsp; + ElastiCache for Redis: Clusters <br>&emsp; + ElastiCache nodes <br>&emsp; + ElastiCache for Redis shards <br> - **Thực hành:** <br>&emsp; + Tạo access key để cấu hình AWS CLI + Sử dụng AWS Console và CLI để tạo ElastiCache cluster <br>&emsp; + Dùng AWS SDK để ghi và đọc dữ liệu trên ElastiCatche: <br>&emsp;&nbsp;&nbsp; + Tạo và kết nối với Clusters <br>&emsp;&nbsp;&nbsp; + Set and Get strings <br>&emsp;&nbsp;&nbsp; + Set and Get a hash with multiple items <br>&emsp;&nbsp;&nbsp; + Publish (write) and subscribe (read) <br>&emsp;&nbsp;&nbsp; + Write and read from a stream       | 15/08/2025   | 15/08/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 6:


