---
title: "Blog 2"
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# Tự động hóa việc tạo vector embedding trong  Aurora PostgreSQL bằng  Bedrock
bởi **Domenico di Salvia** và **Andrea Filippo La Scola**  | vào **ngày 05 tháng 09 năm 2025** | trong Advanced (300),  Amazon Aurora, Amazon Bedrock, Technical How-to | Permalink 

Vector embeddings đã thay đổi sâu sắc cách chúng ta tương tác với dữ liệu phi cấu trúc trong các ứng dụng sử dụng **AI tạo sinh** . Embeddings là các biểu diễn toán học giúp hỗ trợ tìm kiếm ngữ nghĩa (semantic search), hệ thống gợi ý (recommendations), và nhiều tác vụ xử lý ngôn ngữ tự nhiên khác bằng cách nắm bắt bản chất của văn bản, hình ảnh và nội dung khác dưới dạng mà máy có thể xử lý hiệu quả. Trong các ứng dụng sử dụng **Retrieval-Augmented Generation (RAG)** hoặc các giải pháp AI khác, việc duy trì embeddings được cập nhật khi dữ liệu thay đổi là rất quan trọng để đảm bảo kết quả tìm kiếm và gợi ý phản ánh đúng ý nghĩa.

Mặc dù  **Bedrock** cung cấp các **giải pháp RAG quản lý sẵn**, nhiều tổ chức có yêu cầu cụ thể dẫn đến việc họ xây dựng giải pháp cơ sở dữ liệu vector tùy chỉnh, dùng **PostgreSQL** kết hợp **extension pgvector**. Trong bài viết này, tác giả trình bày nhiều cách để tự động sinh embeddings trong  **Aurora PostgreSQL** khi dữ liệu được chèn hoặc cập nhật. Mỗi cách có những đánh đổi về độ phức tạp, độ trễ, tính đáng tin cậy và khả năng mở rộng để bạn chọn được chiến lược phù hợp cho ứng dụng.

---

## Tổng quan giải pháp
Khi dùng Aurora PostgreSQL với extension pgvector để tạo cơ sở dữ liệu vector, bạn cần một cơ chế tin cậy để sinh hoặc cập nhật embeddings khi dữ liệu thay đổi. Quy trình chung như sau:

1. Phát hiện khi nào dữ liệu mới hoặc được sửa cần embedding.

2. Gửi nội dung đó đến mô hình embedding của  Bedrock (ví dụ: Titan).

3. Nhận vector embedding.

4. Lưu chúng song song với dữ liệu gốc.

Trong bài viết, tác giả sử dụng  Titan làm mô hình nền qua  Bedrock vì nó cung cấp embeddings chất lượng sản xuất mà không cần quản lý hạ tầng bổ sung. Bạn cũng có thể chọn các mô hình khác được hỗ trợ (ví dụ: Cohere Embed, Claude của Anthropic) hoặc thậm chí mô hình tùy chỉnh qua **SageMaker** hoặc thư viện mã nguồn mở.

Yêu cầu tiên quyết
Trước khi triển khai bất kỳ cách nào, bạn cần đảm bảo:
 * Có cụm **Aurora PostgreSQL** đã bật **extension pgvector**.
 * **Cấu hình IAM roles & policies** cho phép truy cập **Bedrock**.
 * Với các giải pháp dùng **AWS Lambda**, cấu hình VPC để Lambda có thể truy cập cả database và Bedrock.
 * Với extension aws_ml, **đảm bảo phiên bản database tương thích**.
 * Với pg_cron, **extension đã được bật và cấu hình**.
 * Tác giả cung cấp kho mã nguồn GitHub kèm AWS CDK stack và code để triển khai môi trường demo.

---

## Các cách triển khai

Bài viết mô tả năm chiến lược tự động hóa, mỗi chiến lược có ưu và nhược điểm:

1. **Database triggers + aws_ml extension (synchronous)**
 * Đơn giản: trigger trong database gọi aws_ml đồng bộ trong cùng transaction để sinh embedding.
 * Có mã ví dụ (PL/pgSQL) cho generate_embedding và trigger store_embedding.
 * Ưu điểm: tính đồng bộ tức thì, ít thành phần bên ngoài.
 * Nhược điểm: làm chậm transaction, giới hạn mở rộng, xử lý lỗi phức tạp, rủi ro timeout.

2. **Database triggers + aws_lambda extension (synchronous)**
 * Trigger gọi một Lambda function đồng bộ, rồi function đó sinh embedding và trả kết quả.
 * Tách logic embedding ra khỏi database nhưng vẫn giữ tính đồng bộ.
 * Ưu điểm: linh hoạt hơn trong Lambda (tiền xử lý / hậu xử lý), quan sát lỗi tốt hơn.
 * Nhược điểm: vẫn chặn transaction, có độ trễ Lambda (cold starts), yêu cầu cấu hình phức tạp.

3. Database triggers + aws_lambda extension (asynchronous)
 * Trigger kích hoạt Lambda bất đồng bộ, trả về ngay mà không chờ embedding hoàn thành.
 * Sau khi embedding được sinh, Lambda sẽ ghi lại vào bảng document_embeddings (ví dụ qua RDS Data API).
 * Ưu điểm: transaction không bị chặn, cải thiện throughput ghi.
 * Nhược điểm: tính nhất quán chậm trễ (eventual consistency), phức tạp trong xử lý lỗi, embedding chậm.

4. SQS queue + Lambda batch processing (asynchronous)
 * Trigger gửi thay đổi vào hàng đợi SQS; Lambda consumer xử lý theo lô (batch) để sinh embeddings.
 * Batching giúp giảm số lần gọi API, tăng khả năng retry, cải thiện độ chịu lỗi.
 * Ưu điểm: khả năng mở rộng cao, robust trong xử lý lỗi, sử dụng API hiệu quả.
 * Nhược điểm: độ trễ giữa thay đổi và embedding lâu hơn, độ phức tạp vận hành cao hơn.

5. Cập nhật định kỳ với pg_cron extention (asynchronous)
 * Dùng pg_cron trong database để lập lịch công việc để định kỳ lấy bản ghi cần xử lý, sinh embeddings theo lô và cập nhật.
 * Không sử dụng trigger, nên không ảnh hưởng giao dịch ghi tài liệu ban đầu.
 * Ưu điểm: kiến trúc đơn giản, ít phụ thuộc bên ngoài.
 * Nhược điểm: embedding chậm trễ, overhead batch, ảnh hưởng tải database khi chạy cron.

---

## Các yếu tố thiết kế cần cân nhắc
Khi lựa chọn cách triển khai cho môi trường sản xuất, bạn nên cân nhắc:
 * Giới hạn tốc độ API của  Bedrock các cuộc gọi thường xuyên có thể cần throttling hoặc batching.
 * Giới hạn token trong mô hình embedding  văn bản dài có thể cần chia nhỏ.
 * Chi phí  phụ thuộc vào giao dịch Lambda API, dịch vụ AWS sử dụng.
 * Độ trễ với tính đồng bộ  mỗi cách có đánh đổi riêng.
 * Thao tác ghi vào database  các cách đồng bộ có thể làm giảm hiệu năng khi tải cao.
 * Xử lý lỗi  kiến trúc bất đồng bộ hoặc có hàng đợi dễ hỗ trợ retry hơn.
 * Bảo trì chỉ mục  các chỉ số vector có thể xuống hiệu năng theo thời gian, cần tối ưu định kỳ.

## Cây quyết định
Tác giả cung cấp sơ đồ quyết định để giúp bạn chọn chiến lược tự động embedding dựa trên nhu cầu ứng dụng (độ trễ, tính đồng bộ, độ phức tạp). Bắt đầu từ các cách đơn giản (ví dụ: cách 1 hoặc 5) rồi mở rộng khi nhu cầu tăng lên.

Họ cũng lưu ý rằng cần bảo trì chỉ mục vector — tuỳ loại chỉ mục, việc bảo trì định kỳ cần thiết để giữ hiệu năng và độ nhớ lại trong tìm kiếm ngữ nghĩa.

Bạn có thể xem mã đầy đủ, scripts triển khai và ví dụ trong kho GitHub được liên kết trong bài viết.

--- 

##  Dọn dẹp 
Để tránh chi phí không cần thiết, tác giả khuyến nghị:
1. Xóa các stack CloudFormation đã triển khai cho demo
2. Xóa các tài nguyên AWS bổ sung bạn đã tạo trong quá trình thử nghiệm

---

## Kết luận
Tự động sinh embedding trong Aurora PostgreSQL giúp cho các tính năng AI như tìm kiếm ngữ nghĩa, gợi ý, truy hồi dữ liệu luôn được cập nhật khi dữ liệu thay đổi. Bằng cách giữ embeddings đồng bộ với dữ liệu, bạn đảm bảo tính liên quan và độ chính xác cho các ứng dụng AI.

Trong bài viết, nhiều cách từ triggers, cron, hàng đợi đến giải pháp batch đều được trình bày với đánh đổi về độ trễ, khả năng mở rộng, tính đồng bộ và độ phức tạp vận hành. Lựa chọn tối ưu phụ thuộc vào nhu cầu ứng dụng của bạn — chấp nhận độ trễ, lượng ghi cao hay chi phí vận hành.

Bạn có thể vào kho GitHub trong bài viết để xem giải pháp đầy đủ và mã nguồn. Các tác giả rất hoan nghênh đóng góp hoặc phản hồi qua issues hoặc pull requests.


## Tác Giả

|
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Andrea Filippo La Scola ![Image](/images/2-Proposal/andrea.png)| **Andrea** là Kiến trúc sư Giải pháp Đối tác (Partner Solutions Architect) tại AWS, chuyên về **phân tích dữ liệu** và **kiến trúc serverless**. Anh hỗ trợ các đối tác và khách hàng của AWS tại **Ý** trong việc thiết kế các giải pháp sáng tạo dựa trên các dịch vụ của AWS. | 
| Domenico di Salvia ![Image](/images/2-Proposal/domenico.png) | Domenico là **Kiến trúc sư Giải pháp Chuyên gia về Cơ sở dữ liệu Cấp cao (Senior Database Specialist Solutions Architect)** tại AWS. Trong vai trò này, Domenico làm việc với các khách hàng ở **khu vực EMEA** (Châu Âu, Trung Đông và Châu Phi), cung cấp **hướng dẫn và hỗ trợ kỹ thuật** cho các dự án cơ sở dữ liệu. Anh giúp họ **nâng cao giá trị của giải pháp** khi sử dụng hoặc di chuyển lên AWS, bằng cách thiết kế các kiến trúc cơ sở dữ liệu trong đám mây AWS có **khả năng mở rộng, bảo mật, hiệu suất cao, bền vững, tiết kiệm chi phí và đáng tin cậy**. | 