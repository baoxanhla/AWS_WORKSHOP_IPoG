---
title: "Blog 1"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Bắt đầu với healthcare data lakes: Sử dụng microservices

Các tổ chức có nhiều chi nhánh thường gặp thách thức lớn trong việc quản lý hệ thống tệp phân tán, đặc biệt khi sử dụng hạ tầng tại chỗ (on-premises) truyền thống. Việc duy trì khả năng chia sẻ tệp mượt mà giữa các vị trí địa lý khác nhau, đồng thời đảm bảo tính bảo mật, hiệu quả trong quản lý dữ liệu và xác thực người dùng đáng tin cậy, ngày càng trở nên phức tạp trong bối cảnh số hóa hiện nay.

Amazon FSx for NetApp ONTAP giải quyết những thách thức này bằng cách cung cấp một giải pháp **cloud-native được quản lý hoàn toàn**, mang lại khả năng lưu trữ tệp hiệu năng cao với **tích hợp sẵn tính năng sao chép dữ liệu (replication), đồng bộ tự động và bộ nhớ đệm thông minh (intelligent caching)**.

Trong bài viết này, nhóm tác giả chia sẻ cách một khách hàng đã triển khai **FSx for ONTAP** với cấu hình **Multi-AZ**, sử dụng **NetApp FlexCache** cho bộ nhớ đệm cục bộ và thực hiện di chuyển dữ liệu bằng **SnapMirror**. Trong quá trình này, họ thực hiện các bài kiểm tra hiệu năng, phân tích các đánh đổi trong thiết kế kiến trúc và đưa ra so sánh chi phí — cho thấy mức **giảm 28% chi phí sở hữu tổng thể (TCO)** so với giải pháp tại chỗ truyền thống.

---

## Hướng dẫn kiến trúc

Kiến trúc cốt lõi của giải pháp xoay quanh việc triển khai **Amazon FSx for NetApp ONTAP** trong mô hình **Multi-AZ cluster** trải rộng trên hai Vùng sẵn sàng (Availability Zones), nhằm đảm bảo tính sẵn sàng cao và khả năng chịu lỗi.

Các chi nhánh kết nối tới FSxN thông qua các **kết nối VPN bảo mật**, truy cập dữ liệu thông qua **ONTAP FlexCache volumes** được triển khai tại môi trường on-prem hoặc VMware. Các bộ nhớ đệm này giúp **giảm băng thông và cải thiện tốc độ phản hồi** nhờ phục vụ dữ liệu được truy cập thường xuyên ngay tại chỗ.



**Kiến trúc giải pháp bây giờ như sau:**

> *Hình 1. Kiến trúc tổng thể; những ô màu thể hiện những dịch vụ riêng biệt.*

---

Mặc dù thuật ngữ *microservices* có một số sự mơ hồ cố hữu, một số đặc điểm là chung:  
- Chúng nhỏ, tự chủ, kết hợp rời rạc  
- Có thể tái sử dụng, giao tiếp thông qua giao diện được xác định rõ  
- Chuyên biệt để giải quyết một việc  
- Thường được triển khai trong **event-driven architecture**

Khi xác định vị trí tạo ranh giới giữa các microservices, cần cân nhắc:  
- **Nội tại**: công nghệ được sử dụng, hiệu suất, độ tin cậy, khả năng mở rộng  
- **Bên ngoài**: chức năng phụ thuộc, tần suất thay đổi, khả năng tái sử dụng  
- **Con người**: quyền sở hữu nhóm, quản lý *cognitive load*

---

## Lựa chọn công nghệ và phạm vi giao tiếp

| Phạm vi giao tiếp                        | Các công nghệ / mô hình cần xem xét                                                        |
| ---------------------------------------- | ------------------------------------------------------------------------------------------ |
| Trong một microservice                   | Amazon Simple Queue Service (Amazon SQS), AWS Step Functions                               |
| Giữa các microservices trong một dịch vụ | AWS CloudFormation cross-stack references, Amazon Simple Notification Service (Amazon SNS) |
| Giữa các dịch vụ                         | Amazon EventBridge, AWS Cloud Map, Amazon API Gateway                                      |

---

## The pub/sub hub

Việc sử dụng kiến trúc **hub-and-spoke** (hay message broker) hoạt động tốt với một số lượng nhỏ các microservices liên quan chặt chẽ.  
- Mỗi microservice chỉ phụ thuộc vào *hub*  
- Kết nối giữa các microservice chỉ giới hạn ở nội dung của message được xuất  
- Giảm số lượng synchronous calls vì pub/sub là *push* không đồng bộ một chiều

Nhược điểm: cần **phối hợp và giám sát** để tránh microservice xử lý nhầm message.

---

## Core microservice

Cung cấp dữ liệu nền tảng và lớp truyền thông, gồm:  
- **Amazon S3** bucket cho dữ liệu  
- **Amazon DynamoDB** cho danh mục dữ liệu  
- **AWS Lambda** để ghi message vào data lake và danh mục  
- **Amazon SNS** topic làm *hub*  
- **Amazon S3** bucket cho artifacts như mã Lambda

> Chỉ cho phép truy cập ghi gián tiếp vào data lake qua hàm Lambda → đảm bảo nhất quán.

---

## Front door microservice

- Cung cấp API Gateway để tương tác REST bên ngoài  
- Xác thực & ủy quyền dựa trên **OIDC** thông qua **Amazon Cognito**  
- Cơ chế *deduplication* tự quản lý bằng DynamoDB thay vì SNS FIFO vì:
  1. SNS deduplication TTL chỉ 5 phút
  2. SNS FIFO yêu cầu SQS FIFO
  3. Chủ động báo cho sender biết message là bản sao

---

## Staging ER7 microservice

- Lambda “trigger” đăng ký với pub/sub hub, lọc message theo attribute  
- Step Functions Express Workflow để chuyển ER7 → JSON  
- Hai Lambda:
  1. Sửa format ER7 (newline, carriage return)
  2. Parsing logic  
- Kết quả hoặc lỗi được đẩy lại vào pub/sub hub

---

## Tính năng mới trong giải pháp

### 1. AWS CloudFormation cross-stack references
Ví dụ *outputs* trong core microservice:
```yaml
Outputs:
  Bucket:
    Value: !Ref Bucket
    Export:
      Name: !Sub ${AWS::StackName}-Bucket
  ArtifactBucket:
    Value: !Ref ArtifactBucket
    Export:
      Name: !Sub ${AWS::StackName}-ArtifactBucket
  Topic:
    Value: !Ref Topic
    Export:
      Name: !Sub ${AWS::StackName}-Topic
  Catalog:
    Value: !Ref Catalog
    Export:
      Name: !Sub ${AWS::StackName}-Catalog
  CatalogArn:
    Value: !GetAtt Catalog.Arn
    Export:
      Name: !Sub ${AWS::StackName}-CatalogArn
