+++
author = "Hugo Authors"
title = "Lab 04: Hiểu về web server."
date = "2020-09-25"
description = "Hiểu về web server."
tags = [
    "web server",
	"Lab 04"
]
+++
DNS & Registering DN
<!--more-->

### Web server là gì ?
Web server có nghĩa là máy chủ web, là máy tính lớn được kết nối với tập hợp mạng máy tính mở rộng. Máy chủ chứa toàn bộ dữ liệu mà nó được giao quyền quản lý. Mỗi máy chủ có một IP riêng và có thể đọc đa dạng ngôn ngữ như HTML, HTM, File,… 


Máy chủ có dung lượng lớn và tốc độ rất cao để có thể lưu trữ và vận hành tốt kho dữ liệu trên internet. Thông qua cổng giao tiếp riêng biệt của mỗi máy chủ mà hệ thống máy tính có khả năng hoạt động trơn tru hơn. Máy chủ phải đảm bảo hoạt động liên tục để có thể cung cấp dữ liệu cho mạng lưới máy tính của nó.

Web server có thể là phần cứng hoặc phần mềm cũng có thể bao gồm cả hai. 

 . Phần cứng: Máy chủ web là một máy tính lưu trữ các file ảnh, tài liệu HTML, CSS, file JavaScript của một website và chuyển chúng tới thiết bị của End-user. Máy chủ được kết nối internet và truy cập thông qua một tên miền như Mozilla.org.
 . Phần mềm: Web server gồm một số phần điều khiển người dùng truy cập đến file lưu trữ trên một máy chủ HTTP. Máy chủ HTTP là một phần mềm, nó có khả năng hiểu được các địa chỉ website (URL) và giao thức trình duyệt sử dụng để xem các website (HTTP).

 
Bất cứ khi nào một trình duyệt cần đến file được lưu trữ trên máy chủ, trình duyệt gửi yêu cầu file đó thông qua HTTP. Khi yêu cầu tới đúng máy chủ (phần cứng), HTTP (phần mềm) sẽ gửi tài liệu được yêu cầu trở lại thông qua HTTP.