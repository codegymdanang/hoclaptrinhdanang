---
layout: blog
title: Triển khai ứng dụng Spring trên heroku
slug : spring-database-heroku
category: devops
tags: [cicd]
summery: Triển khai ứng dụng Spring trên heroku   
image: /images/blog/cicd.png
description : Triển khai dự án spring trên heroku. Hiểu được các khái niệm domain là gì. Hosting là gì trong lập trình web.
youtubeId: gdt4DODk5o4
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn, hôm nay anh sẽ hướng dẫn cách <b>triển khai một ứng dụng spring và database</b> trên server <b>Heroku</b>. 

<br>
# **1. Hosting là gì**

Khi mình phát triển ứng dụng và chạy ứng dụng trên máy của mình thì mình hay nhập url là http://localhost:8080. Lúc này chỉ có một mình có thể xem được trang web ứng dụng của mình. Người dùng không thể truy cập được trang web của mình. Nghĩa là mình đang hosting cái web trên cái máy localhost của mình. Trong cái máy localhost của mình sẽ có RAM, CPU , SDK , Mysql và các thư viện khác để ứng dụng có thể chạy được.

Câu hỏi đặt ra nếu mình muốn triển khai ứng dụng cho tất cả mọi người cùng vào xem được thì làm thế nào. Thông thường mình sẽ mua 1 con server. Con server này thì sẽ có nhiều nhà cung cấp cho mình ví dụ như nhà cung cấp amazon , digital ocean hay ovh. Khi mình mua server của họ tuỳ vào cấu hình mà mình phải trả tiền. Như 1G /Ram  là 5 USD/tháng . 10 G Ram là 10USD/tháng. Tuỳ theo mình muốn mua server mạnh hay yếu mà số tiền sẽ trả nhiều hay ít. Sau khi mua server thì nhà cung cấp sẽ gửi cho mình 1 email về username, password để login vào server , đồng thời cung cấp cho mình 1 IP duy nhất . Ví dụ là 192.168.1.2 . Khi đã có server thì mình login vào server và cài đặt các phần mềm như SDK , Mysql , các thư viện mà ứng dụng web mình cần. Nó giống y chang cách mình triển khai trên máy local vậy.

Sau khi triển khai xong thì mình hoàn toàn có thể xem trang web bất cứ đâu với link http://192.168.1.2:8080 (địa chỉ IP do nhà cung cấp phát cho mình khi mình mua server).

<br>
# **2. Domain là gì**

Như các em thấy ở trên để vào được ứng dụng thì người dùng phải gõ số IP (192.168.1.2) cái này rất bất tiện vì không phải ai cũng nhớ IP mà vô trang web mình . Thay vào đó mình có thể đặt cho nó một cái tên như http://levunguyen.com lúc đó nó sẽ hiển thị trang web mình lên. Như vậy đọc levunguyen.com là dể nhớ hơn IP 192.168.1.2. Để làm được việc này chúng ta có thể mua domain trên mạng. Thông thường anh hay mua trên godaddy hoặc PA Việt Nam. Một domain nếu chưa có thì mua thì giá tầm 198.000/năm đến 1.000.000 /năm . Sau khi mua domain xong mình vào trang sản phẩm của mình và cấu hình lại DNS trỏ tới server 192.168.1.2. Như vậy khi người dùng gõ vào http://levunguyen.com thì nó sẽ trỏ tới server (192.168.1.2)

<br>
# **3. Các bước chuẩn bị để triển khai ứng dụng heroku**

Heroku là một nền tảng điện toán đám mây (cloud) cho phép mình triển khai ứng dụng lên server đó mà không mất phí. Tuy nhiên vẫn có phiên bản trả phí từ 7 USD tới 250 USD . Khi dùng bản trả phí thì mình có nhiều chức năng hơn. Trong bài này thì mình dùng bản miễn phí

Heroku hỗ trợ rất nhiều ngôn ngữ như java , php , ruby , nodejs cũng như các loại database postgress , mysql

- Bước 1 : Tạo account trên Heroku

Các em lên trang https://www.heroku.com/home và đăng ký một account. Cái này hoàn toàn miễn phí .  

- Bước 2 : Cài đặt heroku cli để có thể thao tác với Heroku server

Chúng ta sẽ sử dụng heroku cli để tạo ứng dụng , triển khai ứng dụng trên heroku. Có rất nhiều version tương ứng cho Mac , Window hay Ubuntu tại đây https://devcenter.heroku.com/articles/heroku-cli

- Bước 3 : Sau khi cài đặt xong chúng ta hay xem video dưới đây

Video hướng dẫn cách triển khai ứng dụng spring boot và database trên Heroku

{:refdef: style="text-align: center;"}
{% include youtubePlayer.html id=page.youtubeId %}
{: refdef}
