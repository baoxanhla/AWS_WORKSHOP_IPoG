---
title: "Worklog Tuần 5"
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5: 

* Hiểu các dịch vụ bảo mật trên AWS, các nguyên tắc bảo mật cốt lõi của AWS  
* Quản lý danh tính, quyền truy cập và xác thực người dùng an toàn trên AWS.
* Bảo vệ và vận hành dữ liệu bằng các cơ chế mã hóa và quản lý dữ liệu.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tìm hiểu về mô hình chia sẽ trách nhiệm <br>&emsp; + Trách nhiệm của "AWS" và của "Khách hàng" <br>&emsp; + Trách nhiệm bảo mật cuả từng loại hình dịch vụ <br> - Tìm hiểu cơ bản Amazon identity and acess Management: <br>&emsp; + Root Account <br>&emsp; + AWS IAM <br>&emsp; + Chủ thể IAM <br>&emsp; + IAM User <br>&emsp; + IAM policy <br>&emsp; + IAM role <br>&emsp; + IAM permission boundary.       | 06/10/2025   | 06/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - **Thực hành**: <br>&emsp; + Tạo IAM Group, IAM User, IAM Role và Assume Role <br>&emsp; + Tạo User quản trị EC2, User quản trị RDS và group quản trị <br>&emsp; + Cấu hình IAM Role Condition <br>&emsp;&nbsp;&nbsp; + Tạo IAM Role có quyền Admin <br>&emsp;&nbsp;&nbsp; + Tạo IAM User <br>&emsp;&nbsp;&nbsp; + Câu hình Switch role <br>&emsp;&nbsp;&nbsp; + Giới hạn theo IP hoặc thời gian <br>&emsp; + Giới hạn quyền của User <br>&emsp;&nbsp;&nbsp; + Tạo policy giới hạn quyền <br>&emsp;&nbsp;&nbsp; + Tạo IAM giới hạn <br>&emsp;&nbsp;&nbsp; + Kiểm tra User giới hạn <br>&emsp; + Dọn dẹp tài nguyên     | 07/10/2025   | 07/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Tìm hiểu cách dùng Tag và Resource  Groups: <br>&emsp; + Tag <br>&emsp; + AWS Resource Groups <br> - **Thực hành**: <br>&emsp; + Sử dụng Tag bằng console: tạo EC2 với Tag, thêm hoặc xóa Tag và tạo tài nguyên theo Tag <br>&emsp; + Sử dụng Tag bằng CLI <br> &emsp; + Tạo Resource Group <br>&emsp; + Quản lý truy cập vào dịch vụ EC2 Resource Tag với AWS IAM <br>&emsp;&nbsp;&nbsp; + Tạo IAM User, IAM Policy và IAM Role <br>&emsp;&nbsp;&nbsp; + Chuyển Role <br>&emsp;&nbsp;&nbsp; + Kiểm tra IAM Policy: Truy cập vào AWS Region được/không cho phép, sử dụng Resource Tag với giá trị không thỏa mản điều kiện, chỉnh sửa Resource Tag trên EC2 và kiểm tra chính sách <br>&emsp; + Tạo IAM policy, IAM Role và kiểm tra IAM Role <br>&emsp; + Dọn dẹp tài nguyên.  | 08/10/2025   | 08/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Tìm hiểu cơ bản Amazon Congnito: <br>&emsp; + User Pool <br>&emsp; + Identity Pool <br> - Tìm hiểu về AWS Organization <br> - Tìm hiểu về AWS identity center (SSO) <br> - Tìm hiểu về AWS Key Management Service (KMS) <br> - Tìm hiểu về AWS Security Hub <br> - **Thực hành**: <br>&emsp; + Kích hoạt Securiy Hub <br>&emsp; + Điểm từng bộ tiêu chuẩn <br>&emsp; + Dọn dẹp tài nguyên. | 09/10/2025   | 09/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Thực hành:** <br>&emsp; + Sử dụng AWS SSO <br>&emsp;&nbsp;&nbsp; + Tạo AWS Account trong AWS Organizations, thiết lập organization Unit <br>&emsp;&nbsp;&nbsp; + Thiết lập AWS SSO và kiểm tra <br>&emsp; + Mã hóa với AWS KMS <br>&emsp;&nbsp;&nbsp; + Tạo Policy và Role <br>&emsp;&nbsp;&nbsp; + Tạo Group và User <br>&emsp;&nbsp;&nbsp; + Tạo Key Management Sevice <br>&emsp;&nbsp;&nbsp; + Tạo bucket và upload dữ liệu lên Amazon S3 <br>&emsp;&nbsp;&nbsp; + Tạo AWS CloudTrail để ghi nhật ký và Amazon Athena để truy xuất dữ liệu <br>&emsp;&nbsp;&nbsp; + Kiểm thử và chia sẽ dữ liệu mã hóa trên S3 <br>&emsp; + Dọn dẹp tài nguyên | 10/10/2025   | 10/10/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 5:

* Hiểu rõ hơn về mô hình bảo mật của AWS:
  * Trách nhiệm bảo mật sẽ thay đổi theo từng loại dịch vụ, ví dụ: 
    * AWS sẽ chịu trách nhiệm bảo mật của cloud và quản lí hoàn toàn bởi AWS (hạ tầng, phần cứng...)
    * Khách hàng sẽ chịu trách nhiệm cấu hình bảo mật cho dữ liệu/ứng dụng của học (cấu hình dịch vụ, quyền truy cập, dữ liệu, mã hóa…)
  * Biết được IAM, KMS có vai trò quan trọng trong bảo mật AWS

* Hiểu và biết cách sử dụng AWS IAM:
  * nắm được các khái niệm: Root Account, IAM User, IAM Group, IAM Role, IAM Policy, Permission Boundary.
  * Biết tạo và quản lý IAM cơ bản, phân quyền theo nguyên tắc least privilege, sử dụng Role để tăng bảo mật. 

* Biết sử dụng Tag để kiểm soát và quản lý truy cập:
  * Biết sử dụng Tag cho dịch vụ cơ bản qua Console và CLI
  * Tạo được Resource Groups để gom tài nguyên theo thẻ
  * Kiểm thử các trường hợp bị deny do sai Region, sai Tag hoặc không thỏa điều kiện IAM Policy.

* Hiểu được vai trò của AWS Cognito:
  * User Pool: quản lý tài khoản người dùng và quá trình đăng nhập
  * Identity Pool: cấp AWS temporary credentials để ứng dụng truy cập các dịch vụ AWS.

* Biết cách sử dụng AWS Organizations và Identity Center:
    * Biết tạo OU và nắm các nguyên tắc vận hành môi trường multi-account như: tách biệt môi trường, quản lý tập trung, áp chính sách bảo mật thống nhất.
    * Biết thiết lập AWS SSO, tạo Permission Set và đăng nhập vào các tài khoản con từ một danh tính duy nhất.

* Biết dùng AWS KMS để mã hóa và bảo vệ dữ liệu
* Biết kích hoạt và sứ dụng AWS Security Hub để đánh giá các tiểu chuẩn bảo mật, hiểu lổi và cải thiện


