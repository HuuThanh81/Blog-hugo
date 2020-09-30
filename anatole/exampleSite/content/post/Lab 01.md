+++
author = "Hugo Authors"
title = "Lab 01: Hiểu về DNS"
date = "2020-09-25"
description = "Sample article showcasing basic Markdown syntax and formatting for HTML elements."
tags = [
    "DNS",
    "Redistering DN",
]
categories = [
    "DNS",
    "Lab 01",
]
series = ["Themes Guide"]
aliases = ["migrate-from-jekyl"]
+++

DNS & Registering DN
<!--more-->

### 1. DNS là viết tắt của các chữ nào?

Domain Name System: Hệ thống tên miền hay Hệ thống phân giải (resolve) tên miền.

### 2. DNS dùng để làm gì?
DNS dùng để lưu trữ các tên miền (domain name, ví dụ www.google.com), cung cấp dịch vụ chuyển đổi từ địa chỉ dạng chuỗi (tên miền) sang địa chỉ dạng số (IP) và ngược lại (ví dụ www.google.com <> 216.58.221.228).

### 3. Hãy truy cập 3 trang web mà không cần dùng tới tên miền (domain name)?
Thực hiện lệnh ping tên miền trong cửa sổ cmd, có được địa chỉ IP của tên miền, nhập địa chỉ IP vào đường dẫn của trình duyệt.

google.com : 172.217.26.142

gmail.com : 172.217.26.133

facebook.com : 157.240.7.35
### 4. Tên miền cấp 1, cấp 2, cấp 3 là gì? cho ví dụ mỗi loại?
Tên miền cấp 1 cũng là tên miền quốc tế, được dùng chung cho nhiều quốc gia, mỗi tên miền đại diện cho một lĩnh vực, một ngành nghề, hay một khu vực địa lý. Ví dụ: .com, .net, .org, .mil, .edu, .gov, .asia, .eu


Tên miền cấp 2 cũng là tên miền quốc gia, thông thường mỗi quốc gia sẽ có một tên miền riêng, gồm hai kí tự. Ví dụ: .vn (Việt Nam), .cn (Trung Quốc), .uk (Anh), .us (Mỹ).


Tên miền cấp 3 là tên miền kết hợp giữa tên miền cấp 2 và tên miền cấp 1. Ví dụ: .com.vn, .edu.vn, .edu.uk, .com.us

### 5. Tên miền quốc tế là gì? cho 3 ví dụ?
Tên miền quốc tế: do Trung tâm quản lý tên miền quốc tế cấp. 
>Ví dụ thường có đuôi là .com, .net, .biz, .info, .org</p>

### 6. Tên miền “nội địa” hay quốc gia là gì? cho 3 ví dụ?
Tên miền quốc gia (nội địa): do Trung tâm quản lý tên miền của mỗi quốc gia quản lý. 
> Ví dụ tên miền của Việt Nam có đuôi dạng .vn, .com.vn, edu.vn, gov.vn. Các tên miền này do VNNIC quản lý.</p>

### 7. DNS server addresses trong cạc mạng máy tính dùng để làm gì? Tại sao lại có Preferred DNS server/Alternate DNS server?
Để thiết lập địa chỉ của máy phân giải tên miền. Một  cái chính và một cái dự phòng.

### 8. Trong cạc mạng, không điền thông tin trong DNS server, có truy cập được trang web không? chứng minh?
Cạc mạng sẽ tự động chuyển sang chế độ lấy DNS server address tự động.

Nếu cố tình gán một DNS server address không tồn tại thì không thể truy cập trang web.

### 9. “8.8.8.8” là gì?

Là DNS server address của Google

### 10. Sau khi người dùng gõ vào trình duyệt https://www.w3schools.com/, gõ phím Enter.Viết lại quá trình một trình duyệt lấy trang web về?

1. Dựa vào thông tin DNS server address, trình duyệt gửi một gói tin để phân giải tên trang web sang IP.
2. Gửi một gói tin yêu cầu nội dung trang web (index.html) tới Web server.
3. Web server gửi nội dung trang web về cho máy client.
4.  Máy client thông dịch (biên dịch) mã nguồn của trang web (HTML, CSS, JavaScript) rồi hiển thị lên trình duyệt.

### 11. Thử cấu hình DNS server: sửa tập tin hosts để khi người dùng truy cập trang tuoitre.vn, nội dung trình duyệt sẽ hiển thị thông báo lỗi “không thể truy cập được trang tuoitre.vn”

