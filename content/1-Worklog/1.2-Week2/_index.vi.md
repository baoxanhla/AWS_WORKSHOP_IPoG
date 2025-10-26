---
title: "Worklog Tuần 2"
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:

* Thiết kế và triển khai VPC theo tiêu chuẩn AWS Well-Architected Framework
* Cấu hình các thành phần bảo mật mạng quan trọng
* Thiết lập kết nối an toàn giữa môi trường on-premise và AWS 

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                    | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tìm hiểu Amazon Virtual Private Cloud (Amazon VPC), Kiến trúc và Phạm vi <br>&emsp; + AWS Region <br>&emsp; + Availability Zones (AZ) <br>&emsp; + Classless Inter-Domain Routing (CIDR) <br> - Tìm hiểu về các thành phần cơ bản của Amazon VPC <br>&emsp; + Subnet <br>&emsp; + Route Table <br>&emsp; + Internet Gateway <br>&emsp; + NAT Gateway <br> - Tìm hiểu về tường lửa trong VPC <br>&emsp; + Security Group <br>&emsp; + Network ACLs <br>&emsp; + Cách dùng Resource Map <br> - **Thực hành:** <br>&emsp; + Tạo VPC <br>&emsp; + Tạo Subnet <br>&emsp; + Tạo Internet gateway <br>&emsp; + Tạo Route Table <br>&emsp; + Tạo Security Group <br>&emsp; + Kích hoạt VPC Flow Logs                                                                                                | 11/08/2025   | 11/08/2025      |
| 3   | - Tìm hiểu EC2 cơ bản <br>&emsp; + Instance types <br>&emsp; + AMI <br>&emsp; + Key pair <br>&emsp; + Thiết lập Network <br>  - Các cách remote SSH vào EC2 <br>  - Tìm hiểu Elastic IP <br> - Tìm hiểu VPC Reachability Analyzer <br> - Tìm hiểu AWS Systems Manager Session Manager và Amazon CloudWatch  | 13/08/2025   | 13/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - **Thực hành:** Triển khai Amazon EC2 với multi-AZ, tạo NAT Gateways và Amazon CloudWatch cho VPC <br>&emsp; + Tạo máy chủ EC2 Public và Private Subnet <br>&emsp; + Kết nối SSH  <br>&emsp; + Tạo và triển khai NAT Gateway <br>&emsp; + Sử dụng Reachability Analyzer <br>&emsp; + Tạo EC2 Instance Connect Endpoint <br>&emsp; + Sử dụng Session Manager <br>&emsp; + Triển khai CloudWatch Monitoring cho Tài nguyên VPC <br>&emsp; + Dọn dẹp tài nguyên: Terminate các EC2 Instance, Xóa NAT Gateway và Elastic IP Address, Xóa VPC Endpoints                                          | 12/08/2025   | 12/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Tìm hiểu AWS Site-to-Site VPN  <br>&emsp; + AWS Site-to-Site VPN <br>&emsp; + Virtual Private Gateway <br>&emsp; + Customer Gateway <br>&emsp; + AWS VPN Tunnel <br> - Tìm hiểu Transit Gateway <br> - Tìm hiểu về VPC Peering                    | 14/08/2025   | 15/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Thực hành:**: <br>&emsp; + Cấu hình Site to Site VPN: Tạo môi trường VPN và cấu hình kết nối VPN <br>&emsp; + Thiết lập VPC Peering <br>&emsp; + Thiết lập Transit Gateway                                                                                        | 15/08/2025   | 15/08/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 2:

* Tạo và cấu hình thành công VPC theo chuẩn AWS Well-Architected Framework: 
  * VPC chính với CIDR IP (10.0.0.0/16)
  * Tạo 2 Subnet: Public và Private nằm ở hai Availability Zone khác nhau (multi-AZ).
  * Route Table, Internet Gateway, và NAT Gateway được cấu hình đầy đủ để đảm bảo các EC2 trong Private Subnet vẫn có thể truy cập Internet an toàn.
  * Kích hoạt VPC Flow Logs và theo dõi lưu lượng mạng trên CloudWatch Logs.

* Biết triển khai và quản lý EC2:
  * Khởi tạo EC2 instance trong Public và Private Subnet, gán Elastic IP cho máy chủ Public.
  * Truy cập EC2 qua SSH, Instance Connect, và Session Manager (không cần Public IP).
  * Biết giám sát hoạt động EC2 thông qua Amazon CloudWatch (metric CPU, network, status check).

* Cấu hình được Security Group và Network ACLs để bảo mật 
  * Security Group – bảo vệ cấp instance.
  * Network ACL – bảo vệ cấp subnet.
* Biết được CloudWatch Alarm để cảnh báo khi EC2 có lưu lượng hoặc CPU bất thường.

* Nắm được và thực hành cấu hình AWS Site-to-Site VPN để kết nối an toàn giữa AWS và on-premises:
  * Tạo Virtual Private Gateway (VGW) gắn với VPC.
  * Tạo Customer Gateway (CGW) mô phỏng on-premise environment.
  * Thiết lập IPSec Tunnel hoạt động ổn định giữa AWS và CGW.

* Thực hành VPC Peering để kết nối giữa hai VPC riêng biệt trong cùng Region.
* Tìm hiểu và thiết lập thử nghiệm AWS Transit Gateway.
* Hiểu và áp dụng được AWS Systems Manager trong quản lý hạ tầng không cần SSH trực tiếp.


