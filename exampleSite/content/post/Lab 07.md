+++
author = "Hugo Authors"
title = "Lab 07: Tìm hiểu các thông số liên quan đến một web hosting."
date = "2020-09-25"
description = "web hosting."
tags = [
    "web hosting",
	"Lab 07",
    "hosting"
]
+++
DNS & Registering DN
<!--more-->
# I. Các thông số cơ bản
### 1. Disk Space (Dung lượng) :
 Bất kỳ gói Hosting nào cũng có thông số này, đây là thuật ngữ chỉ sức chứa của Hosting, tương tự như dung lượng của ổ cứng trên máy tính hoặc USB của bạn vậy. Mỗi gói Hosting có một dung lượng khác nhau tùy vào nhu cầu sử dụng, bạn có toàn quyền Up/Down file và mã nguồn lên gói Hosting này miễn sao không vượt quá giới hạn của nó.

### 2. Bandwidth (Băng thông) : 
Băng thông là tổng lưu lượng Up/Down File của Hosting trong 1 tháng. Khi số băng thông khả dụng của Hosting quá giới hạn trong 1 tháng, Website của bạn sẽ báo lỗi 502 Service Temporarily Overloaded. Vì thế bạn phải tính toán hợp lý lượng người truy cập Website trong tháng để lựa chọn Hosting có băng thông nhiều hay ít. Hoặc bạn có thể tham khảo các gói Hosting của DIGISTAR với băng thông không giới hạn.

### 3. Parked Domain : 
Là số tên miền chạy song song với tên miền chính trên Hosting của bạn. Nó xài cùng tài nguyên dữ liệu Host (cùng 1 source web) với tên miền chính. Khi người dùng vào tên miền park domain hoặc tên miền chính thì chúng đều trả về một trang web duy nhất có nội dung giống y như nhau.

### 4. Addon Domain : 
Là số tên miền bổ sung được thêm vào Hosting của bạn. Với Addon Domain, Hosting của bạn sẽ bị cắt nhỏ ra thành nhiều Hosting nhỏ hơn để đáp ứng với số lượng Addon Domain đó. Bạn có thể xài riêng tài nguyên dữ liệu Host (khác source web) với tên miền chính => Bạn có một website mới hoàn toàn, tuy nhiên Hosting của bạn sẽ phải gồng gánh nhiều hơn vì bị cắt nhỏ từ dung lượng cho đến Ram và CPU. Vì thế nếu bạn sử dụng chức năng này thì yêu cầu gói Hosting phải có dung lượng lớn và cấu hình mạnh mẽ.

### 5. Sub Domain (tên miền con) : 
Khi bạn muốn phát triển thêm một lĩnh vực hoặc một chuyên mục mới trên website thì hãy dùng chức năng này. Ví dụ tên miền chính là digistar.vn thì sub domain sẽ là bitcoin.digistar.vn hay batdongsan.digistar.vn. Thường thì các nhà cung cấp Hosting sẽ không giới hạn số sub domain nên bạn có thể tạo bao nhiêu tùy thích.

### 6. Tài khoản Email : 
Là số tài khoản Email khả dụng theo tên miền chạy trực tiếp trên Hosting. Vì đây là Email theo Hosting nên chúng không được đánh giá cao, thường có dung lượng thấp, dễ bị vào black list và kém ổn định.

### 7. Tài khoản FTP : 
Là cổng giao tiếp để bạn truyền tải cũng như quản lý các tệp tin và thư mục như hình ảnh, văn bản, âm thanh, video,… có trên Hosting ngoại trừ Database. Tất cả các gói Host bạn sử dụng có hỗ trợ phần mềm quản lý như CPanel hoặc DirectAdmin đều hỗ trợ FTP qua cổng kết nối mặc định là 21 (cổng này có thể thay đổi nếu nhà cung cấp Hosting đổi port).

### 8. Tài khoản MySQL : 
Là sốlượng cơ sở dữ liệu (Database) của gói Hosting. Thông thường các gói Host giá rẻ sẽ có MySQL là 1 tương ứng với một website được chạy.

## II. Các thông số nâng cao.
### 1. CPU : 
Là thông số của CPU cũng như % CPU đang sử dụng của Host. Thông số này càng cao đến ngưỡng 1/1 thì website sẽ load càng chậm. Thông thường các nhà cung cấp sẽ chia ra nhiều gói với CPU dao động từ 75% – 250%.

### 2. Memory Ram : 
Đây là thông số giống máy tính của bạn. Bất kỳ gói Hosting nào cũng có thông số Ram, nó có thể chung Ram với các Hosting khác hoặc xài một thanh Ram riêng biệt. Chỉ số này càng cao thì website của bạn càng chạy khỏe và mượt mà.

### 3. I/O (Input/Output) : 
Là giới hạn tốc độ truyền tải dữ liệu từ Host đến người dùng và được tính bằng Kb/s. Chỉ số này càng cao thì người dùng sẽ Load website nhanh hơn từ đó tăng trải nghiệm người dùng tốt hơn.

### 4. Number of Process : 
Đây là tổng thông số tiến trình chạy trên Hosting. Thông thường các nhà cung cấp sẽ để ẩn thông tin này và nó sẽ dao động từ 50 – 200 tiến trình. Nếu vượt quá ngưỡng thông số này thì khi người dùng truy cập website sẽ gặp lỗi 500 hoặc 503.

### 5. SSL : 
Chứng chỉ số SSL là một giao thức mã hóa các thông tin trên đường đi từ thiết bị của người dùng đến Website. Mỗi chứng chỉ SSL chỉ được tạo ra cho một website duy nhất. Thông thường các nhà cung cấp lớn luôn cài sẵn SSL miễn phí Let’s Encrypt khi bạn mua bất kỳ gói Hosting nào. Nhưng nếu bạn muốn an tâm về bảo mật cũng như tăng sự chuyên nghiệp cho Website thì nên sắm một con SSL trả phí với đầy đủ chức năng hơn.

### 6. Inodes : 
Là giới hạn số File tối đa có trong thư mục Hosting của bạn. Thông số này thường chỉ xuất hiện trên những Hosting không giới hạn, vì nó là Hosting không giới hạn nên nhà cung cấp sẽ tìm một thông số nào đó để giới hạn nhằm tránh những hành vi phá hoại không gian lưu trữ Hosting. Tuy nhiên ở các gói Hosting thông thường, thông số này thường rất cao (trung bình là 250.000 Inodes) nên bạn đừng quá lo lắng. Nếu bạn có nhu cầu sinh ra file nhiều hơn trên Host thì bạn có thể liên hệ với nhà cung cấp nâng cho bạn nếu lý do của bạn là chính đáng.

### 7. IP riêng : 
Mỗi một Hosting sẽ luôn có một địa chỉ IP mặc định không đổi. Nếu bạn có nhu cầu thì có thể mua thêm 1 IP riêng để xử lý các công việc đặc thù như làm web mail hay làm thêm một website khác IP như Blog/Sites vệ tinh. Thường thì các nhà cung cấp sẽ bán IP khác lớp D vì nó thông dụng, nhưng nếu bạn muốn làm SEO bằng Blog hoặc Sites vệ tinh thì nên mua IP khác lớp C.

### 8. PHP Version : 
Là ngôn ngữ lập trình mà Hosting hỗ trợ tốt nhất cho website với nhiều phiên bản cho bạn lựa chọn. Các nhà cung cấp thường luôn có những phiên bản PHP từ 4x -5x và mới nhất là PHP 7.1. Ngoài ngôn ngữ PHP, những Hosting vẫn luôn hỗ trợ cho các ngôn ngữ lập trình khác như HTML, .NET, JS, Java,…