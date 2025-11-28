---
title: "Worklog Tuần 3"
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:

* Hiểu dịch vụ máy chủ ảo cốt lõi (Amazon EC2) và các thành phần quan trọng trong AWS.
* Hiểu rõ kiến trúc, cơ chế hoạt động và cách quản lý các dịch vụ máy chủ ảo trong AWS.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tìm hiểu về Amazon Elastic Compute Cloud (EC2): <br>&emsp; + Instance type <br>&emsp; + AMI, Backup,keypair <br>&emsp; + Elastic block store <br>&emsp; + Instance store <br>&emsp; + User data <br>&emsp; + Meta data <br>&emsp; + EC2 auto scaling <br>&emsp; + EFS/FSx - Lightsail  MGN                                                                                            | 11/08/2025   | 11/08/2025      |
| 3   | - **Thực hành:** <br>&emsp; + Tạo và kết nối máy chủ EC2 trên Window và linux <br>&emsp; + Tạo Snapshor (Backup) EC2 <br>&emsp; + Cài đặt ứng dụng trên EC2 <br>&emsp; + Sử dụng Tag và Resource group để quản lý tài nguyên <br>&emsp; + Giới hạn sử dụng tài nguyên bằng dịch vụ IAM <br>&emsp; + Dọn dẹp tài nguyên                                 | 12/08/2025   | 12/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Tìm hiểu Amazon CloudWatch <br>&emsp; + Metrics <br>&emsp; + Logs <br>&emsp; + Alarms <br>&emsp; + Dashboard <br> - **Thực hành:** <br>&emsp; + Cấu hình CloudWatch Metrics trên EC2 <br>&emsp; + Phân tích CloudWatch Logs từ các ứng dụng trên EC2 Instances và tạo Metrics Filters <br>&emsp; + Thiết lập CloudWatch Alarms để nhận thông báo <br>&emsp; + Xây dựng CloudWatch Dashboard để tổng hợp trạng thái EC2 <br>&emsp; + Dọn dẹp tài nguyên | 13/08/2025   | 13/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Tìm hiểu EC2 auto scaling <br>&emsp; + Auto scaling group br>&emsp; + Các loại Scaling: manual, scheduled, dynamic br>&emsp; + Launch Template br>&emsp; + Elastic Load Balancer <br> - **Thực hành** <br>&emsp; + Tạo Launch Template cho EC2 <br>&emsp; + Tạo Target Group <br>&emsp; + Tạo Load Balancer <br>&emsp; + Tạo Auto Scaling Group để mở rộng linh hoạt <br>&emsp; + Kiểm tra kết quả của các cơ chế scaling <br>&emsp; + Dọn dẹp tài nguyên            | 14/08/2025   | 15/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Tìm hiểu Amazon Lightsail <br>&emsp; + Lightsail Database <br>&emsp; + Wordpress Instance <br>&emsp; + Prestashop E-Commerce Instance <br>&emsp; + Akaunting Instance <br>&emsp; + Akaunting Instance <br> - **Thực hành:** <br>&emsp; + Triển khai các loại instance và database: Wordpress Instance, Prestashop E-Commerce Instance và Akaunting Instance <br>&emsp; + Sử dụng Lightsail Loadbalancer <br>&emsp; + Tạo Snapshot để backup và khôi phục <br>&emsp; + Dịch chuyển sang instance lớn hơn <br>&emsp; + Dọn dẹp tài nguyên | 15/08/2025   | 15/08/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 3:

* Nắm được kiến trúc và cơ chế hoạt động của Amazon EC2, phân biệt được các loại Instance Type (General Purpose, Compute Optimized, Memory Optimized, Storage Optimized).
* Hiểu cách sử dụng Amazon Machine Image (AMI), Key Pair, Elastic Block Store (EBS), và Instance Store để cấu hình và quản lý máy chủ.
* Biết cách khai thác User Data và Meta Data để tự động hóa cấu hình khi khởi tạo EC2 Instance.
* Hiểu và thực hành với EFS/FSx trong việc lưu trữ và chia sẻ dữ liệu giữa các máy chủ.

* Tạo và kết nối thành công máy chủ EC2 trên cả Windows và Linux.
* Tạo và khôi phục Snapshot (Backup) của EC2.
* Cài đặt ứng dụng web cơ bản trên EC2 instance.
* Sử dụng Tag và Resource Group để phân loại, quản lý tài nguyên hiệu quả.
* Cấu hình IAM để giới hạn quyền truy cập và kiểm soát sử dụng tài nguyên.

* Hiểu rõ các thành phần của Amazon CloudWatch: Metrics, Logs, Alarms, và Dashboard.
* Cấu hình CloudWatch Metrics cho EC2 và tạo Metrics Filters từ log ứng dụng.
* Thiết lập CloudWatch Alarm để nhận cảnh báo khi CPU hoặc lưu lượng mạng vượt ngưỡng.
* Xây dựng CloudWatch Dashboard để tổng hợp và theo dõi trạng thái hệ thống EC2.

* Hiểu rõ cơ chế hoạt động của EC2 Auto Scaling và các loại Scaling: 
  * Manual: tự điều chỉnh số lượng EC2 instance thủ công khi cần thay đổi tài nguyên.
  * Schedual: Tự động thay đổi số lượng instance theo lịch định sẵn, phù hợp với tải mà dự đoán được để tiết kiệm chi phí.
  * Dynamic: Tự động mở rộng hoặc thu hẹp tài nguyên dựa trên các chỉ số CloudWatch như CPU hoặc lưu lượng mạng.
* Biết thiết lập và kiểm tra Auto Scaling Group hoạt động tự động khi tải tăng hoặc giảm.

* Tìm hiểu và triển khai thành công các loại Lightsail Instance:
  * WordPress Instance: website CMS cơ bản.
  * PrestaShop Instance: nền tảng thương mại điện tử.
  * Akaunting Instance: hệ thống quản lý tài chính kế toán.
* Sử dụng Lightsail Database để lưu trữ dữ liệu ứng dụng và Lightsail Load Balancer để phân phối tải và tăng độ sẵn sàng.
* Biết tạo Snapshot để backup dữ liệu và nâng cấp instance sang cấu hình lớn hơn

