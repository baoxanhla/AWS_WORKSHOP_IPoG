---
title: "Worklog Tuần 4"
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

* Hiểu và ứng dụng các dịch vụ lưu trữ dữ liệu trên AWS như S3, Storage Gateway, và Snow Family.
* Nắm vững các cơ chế sao lưu và khôi phục dữ liệu với AWS Backup và Disaster Recovery on AWS.
* Biết cách triển khai giải pháp lưu trữ an toàn, mở rộng và đảm bảo tính sẵn sàng cao cho hệ thống ứng dụng.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tìm hiểu Amazon Simple Storage Service (Amazon S3) <br>&emsp; + S3 Bucket <br>&emsp; + S3 Object <br>&emsp; + Access Point <br>&emsp; + Các lớp lưu trữ: Standard, Standard-IA, Intelligent-Tiering, Glacier + S3 Static Website & CORS + Control Access + Endpoint & Versioning + Object Key & Performance + Glacier: Expedited, Standard, Bulk <br> - **Thực hành:** <br>&emsp; + Tạo S3 Bucket <br>&emsp; + Upload dữ liệu lên S3 <br>&emsp; + Host static wedsite trên S3: bật tính năng static wedsite, Cấu hình Block Public Access và public object <br>&emsp; + Kiểm tra wedsite <br>&emsp; + Tăng tốc wedsite với Cloufront <br>&emsp; + Di chuyển Object và sao chép S3 Object sang region khác <br>&emsp; + Dọn dẹp tài nguyên                                             | 29/09/2025   | 29/09/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Tìm hiểu cách sử dụng AWS Backup để tạo ra một kế hoạch sao lưu cho các tài nguyên đang hoạt động trên AWS <br>&emsp; + Hạ tầng của AWS Backup <br>&emsp; + Backup Plan <br>&emsp; + AWS SNS (Simple Notification Service) <br> - **Thực hành:** <br>&emsp; + Tạo S3 Bucket và triển khai hạ tầng AWS Backup <br>&emsp; + Tạo Backup Plan <br>&emsp; + Thiết lập Nofication <br>&emsp; + Kiểm tra hoạt động <br>&emsp; + Dọn dẹp tài nguyên  | 30/09/2025   | 30/09/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Tìm hiểu Snow Family: + Snowball + Snowball Edge + Snowmobile <br> - Tìm hiểu Storage Gateway <br>&emsp; + Cổng kết nối tập tin (File Gateway) <br>&emsp; + Cổng kết nối ổ đĩa (Volume Gateway) <br>&emsp; + Cổng kết nối băng từ (Tape Gateway)  <br> - Tìm hiểu Disaster Recovery: Recovery Time Object RTO và Recovery Point Object RPO <br>&emsp; + Sao lưu và khôi phụ <br>&emsp; + Pilot Light (Active-Standby) <br>&emsp; + Low Capacity (Active-Active) <br>&emsp; + Full Capacity (Active-Active) <br> - **Thực hành:**  <br>&emsp; + Tạo Storage Gateway <br>&emsp; + Tạo File Shares <br> &emsp; + Kết nối File shares ở máy On-premise <br>&emsp; + Dọn dẹp tài nguyên | 01/10/2025   | 01/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Tìm hiểu về AWS Import / Export <br> - **Thực hành:** <br>&emsp; + Chuẩn bị máy ảo trên VMware Workstation <br>&emsp; + Import máy ảo vào AWS: Export máy ảo từ môi trường on-premises, Upload máy ảo lên AWS, Import máy ảo vào AWS, Khởi chạy EC2 instance từ AMI đã import <br>&emsp; + Export EC2 Instance từ AWS: Cấu hình ACL cho S3 bucket, Export máy ảo từ EC2 Instance, Export máy ảo từ AMI <br>&emsp; + Dọn dẹp tài nguyên  | 02/10/2025   | 02/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Tìm hiểu về Amazon FSx <br> - **Thực hàng:** <br>&emsp; + Tạo môi trường thực hành <br>&emsp; + Tạo một SSD Multi-AZ file system <br>&emsp; + Tạo một HDD Multi-AZ file system <br>&emsp; + Tạo file shares mới <br>&emsp; + Kiểm tra hiệu năng <br>&emsp; + Giám sát hiệu năng <br>&emsp; + kích hoạt chống dữ liệu trùng lặp <br>&emsp; + Kích hoạt shadow copies <br>&emsp; + Quản lý Session người dùng và mở tệp <br>&emsp; + Kích hoạt hạn mức lưu trữ của người dùng <br>&emsp; + Kích hoạt chia sẻ liên tục <br>&emsp; + Scale quy mô thông qua năng suất <br>&emsp; + Scale dung lượng lưu trữ <br>&emsp; + Dọn dẹp tài nguyên.  | 03/10/2025   | 03/010/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 4:

* Hiểu cấu trúc và cách hoạt động của S3 Bucket, Object, Access Point, ACL/Policy, CORS, Versioning, Object Key, các lớp lưu trữ (Standard, IA, Intelligent-Tiering, Glacier).: 
* Triển khai thành công:
  * Tạo bucket, upload object
  * Host static website và cấu hình CloudFront tăng tốc
  * Thiết lập truy cập công khai và kiểm soát truy cập
  * Sao chép dữ liệu cross-region*

* Hiểu và thực hành các giải pháp lưu trữ on-premises tới AWS với Storage Gateway
* Biết được chi tiết về Snow Family và các use-case di chuyển dữ liệu lớn.
* Hiểu và biết cách dùng Amazon FSx: tạo hệ thống Multi-AZ SSD/HDD, quản lý shares, shadow copy, chống trùng lặp, giám sát, mở rộng hiệu năng và dung lượng.

* Nắm được các cơ chế sao lưu và khôi phục dữ liệu trên AWS (AWS Backup & DR)
  * Hiểu kiến trúc AWS Backup, Backup Vault, Backup Plan, và hoạt động lifecycle.
  * Cấu hình thành công: Backup Plan, SNS, Notification, Tự động hóa sao lưu, Kiểm thử restore
  * Hiểu chi tiết về Disaster Recovery:
    * RTO: Thời gian tối đa để khổi phục hệ thống khi xảy ra sự cố
    * RPO: Mức dữ liệu tối đa chấp nhận bị mất tính từ lức xảy ra sự cố
    * Pilot Light:
    * Warm Standby: 
    * Multi-Site Active-Active: 

* Có khả năng triển khai giải pháp lưu trữ an toàn, mở rộng và đảm bảo tính sẵn sàng cao
  * Áp dụng Versioning, Replication (S3) để tăng tính sẵn sàng.
  * Sử dụng Multi-AZ FSx nhằm tạo kiến trúc lưu trữ chịu lỗi (High Availability).
  * Sử dụng CloudFront giúp tối ưu hiệu năng phân phối tệp tĩnh.
  * Hiểu các mô hình DR để thiết kế hệ thống có khả năng khôi phục nhanh khi xảy ra sự cố.
  * Có khả năng scale dung lượng & throughput trên FSx.

* Nâng cao kỹ năng triển khai lưu trữ On-premises tới AWS và ngược lại 
  * Biết cách Import/Export máy ảo: Export VM từ VMware, Upload vào S3, Import thành AMI, Khởi chạy EC2, Xuất EC2 ngược lại thành VM
  * Kết nối File Share từ Storage Gateway vào môi trường on-premise.


