---
title: "Blog 1"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Cách một khách hàng giảm 28% tổng chi phí sở hữu (TCO) cho việc lưu trữ với Amazon FSx for NetApp ONTAP
bởi **Sachin Bawse** và **Vishnu Vashist** | vào **ngày 08 tháng 9 năm 2025** | trong chuyên mục Advanced (300), Amazon FSx for NetApp ONTAP, Best Practices, Healthcare, Technical How-to | Permalink

Các tổ chức có nhiều chi nhánh thường gặp thách thức lớn trong việc quản lý hệ thống tệp phân tán, đặc biệt khi sử dụng hạ tầng tại chỗ (on-premises) truyền thống. Việc duy trì khả năng chia sẻ tệp mượt mà giữa các vị trí địa lý khác nhau, đồng thời đảm bảo tính bảo mật, hiệu quả trong quản lý dữ liệu và xác thực người dùng đáng tin cậy, ngày càng trở nên phức tạp trong bối cảnh số hóa hiện nay.

Amazon FSx for NetApp ONTAP giải quyết những thách thức này bằng cách cung cấp một giải pháp **cloud-native được quản lý hoàn toàn**, mang lại khả năng lưu trữ tệp hiệu năng cao với **tích hợp sẵn tính năng sao chép dữ liệu (replication), đồng bộ tự động và bộ nhớ đệm thông minh (intelligent caching)**.

Trong bài viết này, nhóm tác giả chia sẻ cách một khách hàng đã triển khai **FSx for ONTAP** với cấu hình **Multi-AZ**, sử dụng **NetApp FlexCache** cho bộ nhớ đệm cục bộ và thực hiện di chuyển dữ liệu bằng **SnapMirror**. Trong quá trình này, họ thực hiện các bài kiểm tra hiệu năng, phân tích các đánh đổi trong thiết kế kiến trúc và đưa ra so sánh chi phí — cho thấy mức **giảm 28% chi phí sở hữu tổng thể (TCO)** so với giải pháp tại chỗ truyền thống.

--- 

## Tổng quan giải pháp
Kiến trúc cốt lõi của giải pháp xoay quanh việc triển khai **Amazon FSx for NetApp ONTAP Multi-AZ cluster** trải rộng trên hai Vùng sẵn sàng (Availability Zones), nhằm đảm bảo tính sẵn sàng cao và khả năng chịu lỗi.
Các chi nhánh kết nối tới FSxN thông qua các **kết nối VPN bảo mật**, truy cập dữ liệu thông qua **ONTAP FlexCache volumes** được triển khai tại môi trường on-prem hoặc VMware. Các bộ nhớ đệm này giúp **giảm băng thông và cải thiện tốc độ phản hồi** nhờ phục vụ dữ liệu được truy cập thường xuyên ngay tại chỗ.
Việc di chuyển dữ liệu được thực hiện bằng **NetApp SnapMirror**, đảm bảo sao chép dữ liệu nhất quán từ kho lưu trữ on-prem lên AWS.
> *Hình 1: Hệ thống tệp phân tán với kiến trúc **Amazon FSx** hoặc **NetApp ONTAP**.

![Image](/images/2-Proposal/distributed.png)

Các lớp giao tiếp và bộ nhớ đệm bao gồm:
 * Chi nhánh địa phương → FlexCache volumes (phục vụ dữ liệu nóng)
 * FlexCache → FSx ONTAP origin cluster trên các AZ
 * SnapMirror → sao chép dữ liệu lên FSx, duy trì hiệu quả lưu trữ
Khách hàng cũng tiến hành so sánh hiệu năng: khi truyền một tệp 50 MB, **ONTAP Select cache kết nối FSx** đạt 26,09 giây, so với **24,20 giây trên máy chủ tệp cục bộ**, cho thấy hiệu năng gần tương đương với lưu trữ tại chỗ.

---

## Cân nhắc về độ trễ và ghi lại FlexCache

Tính năng ghi lại (**write-back**) của FlexCache đặc biệt hữu ích khi độ trễ (latency) giữa bộ nhớ đệm chi nhánh và cụm gốc vượt quá **8 ms**. Trong điều kiện đó, bộ nhớ đệm giúp cải thiện hiệu năng ghi dữ liệu đáng kể.

Một số yêu cầu thiết kế cần lưu ý:
 * **CPU & RAM**: Mỗi nút trong cụm gốc cần ít nhất **128 GB RAM** và khoảng **20 vCPUs** để xử lý tải write-back.
 • **Phiên bản ONTAP**: Cụm gốc và cụm cache phải chạy **ONTAP 9.15.1 trở lên** để hỗ trợ write-back.
 • **Giấy phép (Licensing)**: FlexCache (bao gồm cả write-back) đã được tích hợp sẵn, **không cần mua thêm license**.
 • **Cluster peering**: Cụm gốc và cụm cache cần được **kết nối ngang hàng (peered)**, các server virtual machines **SVMs** cũng cần được **vserver-peered** với FlexCache bật.

Những nguyên tắc này giúp đảm bảo bộ nhớ đệm hoạt động ổn định trong các mô hình chi nhánh phân tán.

---

## Giám sát và khả năng hiển thị

Để có cái nhìn chi tiết hơn về hiệu suất và hoạt động của FSx & ONTAP ngoài dữ liệu mặc định trên **Amazon CloudWatch**, giải pháp sử dụng **NetApp Harvest** kết hợp với **Grafana**. Công cụ Harvest thu thập các chỉ số như **hiệu năng, tỷ lệ cache hit, mức độ hiệu quả lưu trữ, và thống kê cấp volume**, giúp quản trị viên có khả năng theo dõi chi tiết và chủ động tối ưu hóa.

---

## Ước tính TCO so với on-premises

Để định lượng lợi ích về chi phí, khách hàng đã mô hình hóa một kịch bản lai (hybrid) để so sánh giữa **FSx for ONTAP** (Multi-AZ, cấu hình SSD + capacity tier tỉ lệ khoảng 30/70, throughput ~256 MB/s) với **hệ thống tại chỗ tương đương**.

Kết quả cho thấy **FSx for ONTAP giúp giảm ước tính 28% tổng chi phí sở hữu (TCO)** so với giải pháp tại chỗ, nhờ giảm chi phí vận hành, tăng hiệu quả lưu trữ, và đơn giản hóa hạ tầng quản lý.

---

## Kết Luận
**Amazon FSx for NetApp ONTAP** là một giải pháp mạnh mẽ cho các hệ thống tệp phân tán, đặc biệt phù hợp với mô hình nhiều chi nhánh.

Thông qua **triển khai Multi-AZ, FlexCache để lưu đệm cục bộ, SnapMirror để di chuyển dữ liệu**, cùng hệ thống **giám sát chi tiết**, kiến trúc này mang lại **hiệu năng gần như cục bộ, độ sẵn sàng cao,** và **giảm 28% TCO so với on-premises**.

Chiến lược triển khai này cho thấy cách tích hợp lưu trữ đám mây hiện đại có thể khắc phục các hạn chế truyền thống về băng thông, tính nhất quán và độ phức tạp vận hành trong các hệ thống phân tán nhiều địa điểm.

---

## Tác Giả

|
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Sachin Bawse ![Image](/images/2-Proposal/Sachin-Bawse.png)| Sachin là **Kiến trúc sư Giải pháp Chuyên gia về Lưu trữ (GTM Specialist Storage Solution Architect) tại Amazon Web Services (AWS)**, nơi anh chuyên về **tối ưu hóa các giải pháp lưu trữ, hỗ trợ di chuyển dữ liệu,** và **nâng cao hiệu suất khối lượng công việc** cho khách hàng. Ngoài công việc, Sachin là một người **đam mê khám phá**, thích **du lịch đến những điểm đến mới, tìm hiểu các nền văn hóa khác nhau** và **thưởng thức ẩm thực đa dạng**. | 
| Vishnu Vashist ![Image](/images/2-Proposal/Vishnu-Vashist.png) | Vishnu Vashist là **Kiến trúc sư Giải pháp Thành công Đối tác (Partner Success Solutions Architect)** trong bộ phận **Đối tác (Partner Org)** của AWS, nơi anh phụ trách các tài khoản thuộc lĩnh vực **Y tế, Chăm sóc sức khỏe, Khoa học đời sống (HCLS)** cũng như **Du lịch, Vận tải và Logistics**. Anh chuyên về **di chuyển và hiện đại hóa hệ thống, hỗ trợ các dự án di chuyển quy mô lớn lên AWS** và **hướng dẫn khách hàng cùng đối tác về thiết kế kiến trúc và hạ tầng trên AWS**. | 