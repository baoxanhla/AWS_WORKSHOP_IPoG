---
title: "Blog 3"
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# Nhóm các bảng cơ sở dữ liệu trong tác vụ AWS Database Migration Service (DMS) cho nguồn là PostgreSQL
bởi **Manojit Saha Sardar** và **Chirantan Pandya** | vào **ngày 05 tháng 9 năm 2025**| trong **Amazon Aurora**, **AWS Database Migration Service, Expert (400), PostgreSQL compatible, RDS for PostgreSQL,** Technical How-to | Permalink

Trong các dự án di chuyển dữ liệu lớn sử dụng **AWS DMS** (Database Migration Service), việc **nhóm các bảng nguồn** vào các tác vụ (tasks) một cách hợp lý là rất quan trọng để đảm bảo hiệu năng tốt và tránh độ trễ trong giai đoạn **full load** hoặc **CDC**. Trong bài viết này, các tác giả hướng dẫn cách phân tích cơ sở dữ liệu PostgreSQL nguồn để xác định kích thước task tối ưu và cách nhóm bảng, giúp bạn lên kế hoạch di chuyển dữ liệu sao cho giảm thiểu độ trễ và tối đa hóa thông lượng. 

---

## Bối cảnh & động lực
Khi di chuyển, có thể xảy ra tình huống một số nhiệm vụ bị chậm hoặc nghẽn do cách nhóm bảng không hợp lý — chẳng hạn gộp quá nhiều bảng nhỏ hoặc trộn bảng rất lớn với bảng nhỏ khác. 
 Sự chậm trễ có thể phát sinh trong cả pha **full load** hoặc khi áp dụng thay đổi theo **CDC** do cạnh tranh tài nguyên, nghẽn I/O, hoặc phân bố tải không đều. 
 Bằng cách phân tích đặc tính bảng và các chỉ số hệ thống, bạn có thể đưa ra lựa chọn sáng suốt về số lượng task DMS, cách gộp bảng, và bảng nào cần tách riêng. 

---

## Tổng quan giải pháp
Cách tiếp cận kết hợp metadata từ database nguồn (catalog, view thống kê) cùng với thông tin phần cứng và tải hoạt động để:
1. Xác định số task DMS thích hợp

2. Phân nhóm bảng vào các task sao cho cân bằng

3. Cô lập các bảng “đặc biệt” (ví dụ: rất lớn, chứa LOB) để tránh ảnh hưởng chéo

Luồng công việc đề xuất:

1. Tạo **control table** trên database nguồn

2. Điền thông tin metadata (kích thước, partition, index, LOB, thống kê DML)

3. Giám sát mức độ thay đổi / tăng trưởng hàng ngày

4.Phân loại bảng theo bước / ưu tiên

5. Gộp bảng vào các nhóm cho mỗi task

6. Triển khai di chuyển theo các nhóm đó

Phương pháp này giúp giảm thiểu độ trễ và đưa ra ước tính về kích thước task chính xác hơn. 

> *Sơ đồ sau minh họa kiến trúc giải pháp.

![Image](/images/2-Proposal/table.png)

## Yêu cầu tiên quyết
Bạn cần:
* Có kiến thức về **AWS DMS** (Database Migration Service) 
* Database PostgreSQL nguồn, và khả năng chạy các script SQL / PL/pgSQL để thu thập metadata 

## Bước 1: Tạo bảng control
Trên database nguồn PostgreSQL, tạo bảng (ví dụ TABLE_MAPPING) để chứa metadata của mỗi bảng ứng cử:
CREATE TABLE TABLE_MAPPING (
  OWNER             VARCHAR(30),
  OBJECT_NAME       VARCHAR(30),
  OBJECT_TYPE       VARCHAR(30),
  SIZE_IN_MB        NUMERIC(12,4),
  STEP              INTEGER,
  IGNORE            CHAR(3),
  PARTITIONED       CHAR(3),
  PART_NUM          INTEGER,
  SPECIAL_HANDLING  CHAR(3),
  PK_PRESENT        CHAR(3),
  UK_PRESENT        CHAR(3),
  LOB_COLUMN        INTEGER,
  GROUPNUM          INTEGER,
  TOTAL_DML         INTEGER
);

Bảng này lưu một dòng cho mỗi bảng (hoặc mỗi phân vùng), chứa các chỉ số như kích thước, số phân vùng, có PK/UK hay không, số cột LOB, tổng số DML, v.v. 

---

## Bước 2: Điền bảng control
Sử dụng catalog hệ thống PostgreSQL và các view thống kê (ví dụ pg_tables, pg_partitioned_table, pg_inherits, và các view thống kê) để thu thập:
* Kích thước bảng, thông tin partitioning

* Số lượng index, có hay không có primary / unique key

* Số cột LOB

* Số lượng DML (insert / update / delete)

* Thống kê phân vùng (min, max, trung bình kích thước)

Điều này giúp bạn có “snapshot” metadata + workload để suy xét khi nhóm bảng. 

--- 

## Bước 3: Giám sát mức độ thay đổi
Theo dõi lượng hoạt động DML trên mỗi bảng theo thời gian. Điều này giúp xác định bảng nào “nóng” (thay đổi nhiều) và bảng nào ít thay đổi, từ đó cân nhắc khi nhóm. 

--- 

## Bước 4: Phân loại bảng / gán bước
Dựa vào kích thước bảng, tần suất thay đổi, nhu cầu xử lý đặc biệt (LOB, thiếu PK), hoặc partitioning, gán step number hoặc mức ưu tiên cho từng bảng. Ví dụ:
* Step 1: bảng nhỏ, thay đổi thấp

* Step 2: bảng trung bình / thay đổi vừa phải

* Step N: bảng rất lớn hoặc thay đổi mạnh

Bạn cũng có thể đánh dấu **IGNORE** cho những bảng không muốn đưa vào task cụ thể, hoặc **SPECIAL_HANDLING** để tách riêng các bảng đặc biệt. 

---

## Bước 5: Gộp bảng vào các task
Dùng bảng control và phân loại bước để nhóm các bảng sao cho:
* Mỗi nhóm có tải cân bằng (kích thước, mức độ thay đổi)
* Bảng rất lớn (ví dụ > 2 TB) có thể được tách riêng
* Bảng chứa LOB hoặc thiếu PK nên được nhóm cẩn trọng hoặc tách riêng
* Các bảng thay đổi nhiều có thể được cách ly để tránh ảnh hưởng lẫn nhau
* Số lượng task không quá nhiều, phù hợp với công suất của replication instance
Mục tiêu là giảm lag, giảm cạnh tranh tài nguyên và phân bố tải đồng đều giữa các task. 

---

## Các yếu tố cần cân nhắc
Khi nhóm và định kích thước task, hãy xem xét:
* **Kích thước đối tượng database**: các bảng cực lớn nên cô lập hoặc xử lý riêng 
* **Partitioned vs non-partitioned**: các bảng phân vùng có thể cho phép di chuyển song song từng phân vùng 
* **Có PK / unique index**: DMS yêu cầu PK/UK để xử lý LOB hoặc tránh trùng lặp 
* **Sử dụng LOB**: các cột LOB làm tăng độ phức tạp và chi phí sao chép — nên cô lập các bảng có LOB nặng 
* **Khối lượng thay đổi (CDC)**: bảng có thay đổi thường xuyên nên được nhóm để tránh nghẽn áp dụng thay đổi 
* **Parallelism & giới hạn tài nguyên**: khả năng của replication instance (CPU, I/O), băng thông mạng, v.v. quyết định số task hiệu quả 

---

## Kiến trúc mẫu & luồng công việc
Bài viết có sơ đồ minh họa cách phân loại nguồn bảng, nhóm và áp dụng các task song song (không thể hiện ở đây). 
Nó cũng mô tả cách bảng control được duy trì trong quá trình di chuyển và dùng để theo dõi tiến độ, cũng như điều chỉnh nhóm khi cần. 

---

## Tóm tắt & khuyến nghị
Bằng cách:
* Phân tích metadata một cách có hệ thống

* Phân loại và gộp bảng dựa trên đặc tính và workload

* Cô lập bảng rủi ro cao (rất lớn, LOB, thiếu PK)

* Cân bằng tải giữa các task

Bạn có thể giảm rủi ro trong di chuyển, dự đoán kích thước task tốt hơn và đạt được migration mượt mà, hiệu suất cao.

---

## Tác Giả

|
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Manojit Saha Sardar ![Image](/images/2-Proposal/manojit.png)| **Manojit** là **kỹ sư cơ sở dữ liệu cấp cao** tại AWS và được công nhận là **chuyên gia trong lĩnh vực** AWS DMS, Amazon RDS và Amazon RDS for PostgreSQL. Trong vai trò của mình tại AWS, anh **hợp tác với khách hàng** để giải quyết các **tình huống truyền dữ liệu khác nhau** và **hỗ trợ xử lý các thách thức** liên quan đến Amazon RDS for Oracle và Amazon RDS for PostgreSQL. | 
| Chirantan Pandya ![Image](/images/2-Proposal/chirantan.png) | **Chirantan** là **kỹ sư cơ sở dữ liệu (AWS Countdown Premium)** và chuyên gia về AWS DMS và Amazon RDS for PostgreSQL. Tại AWS, anh **làm việc chặt chẽ với khách hàng** để cung cấp **hướng dẫn và hỗ trợ kỹ thuật** cho các dự án **di chuyển cơ sở dữ liệu**, cũng như các dự án liên quan đến **Amazon RDS for PostgreSQL và Oracle**. | 


