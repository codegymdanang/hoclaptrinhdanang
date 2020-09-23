---
layout: course-angular
title: Sử dụng Bootstrap   
slug : bootstrap-trong-angular
category: laptrinhweb
tags: [angular]
summery: Sử dụng Bootstrap   
image: /images/blog/angular.png
description : Sử dụng boostrap trong dự án angular. Hướng dẫn cài đặt bootstrap vào dự án Angular. Hướng dẫn các tạo một ứng dụng ANgular và nhúng Bootstrap vào dự án.
youtubeId: 977WIZTAUv8
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người cách <b>sử dụng Bootstrap vào dự án Angular</b> là như thế nào?

# **1 Giới thiệu về Bootstrap**

Boostrap là là một framework opensource gồm có <b>html,css và javascript</b>. Chúng ta sử dụng bootstrap để làm trang web trở nên đẹp hơn. Chúng ta kết hợp với <b>angular</b> để tiết kiệm thời gian. Đồng thời Bootstrap đã dựng sẳn các chức năng hiển thị được trên mobile và các thành phần của web. Nên chúng ta chỉ sử dụng mà thôi.

Ngoài Bootstrap thì còn có rất nhiều framework khác hỗ trợ chúng ta trong việc làm giao diện như <b>Polymer, material , ant design</b>. Tuỳ theo dự án mà ta có thể chọn framework tương ứng. Nhưng theo anh thấy 70% dự án web của anh đều dùng Bootstrap.

# **2 Cài đặt bootstrap cho dự án**

Có 2 cách để mình có thể nhúng Boostrap vào dự án Angular.

- Chúng ta có thể sử dụng <b>Bootstrap từ CDN</b> [tại đây](https://www.bootstrapcdn.com/)
- Chúng ta sử dụng npm (node module) để cài bootstrap trực tiếp vào dự án.

Sự khác nhau giữa CDN và npm là nếu chúng ta dùng CDN thì chúng ta sẽ nhúng đường link bootstrap vào dự án. Khi trang web load lên thì nó sẽ lên mạng và nhúng file bootstrap từ CDN vào trang web. Còn nếu dùng npm thì chúng ta sẽ download sourcecode của boostrap vào trong dự án của mình và chúng ta chỉ link tới file bootstrap trong dự án mình thôi.

## **3 Tạo ứng dụng Angular và sử dụng Bootstrap từ CDN**

- Bước 1 : Cài đặt Angular CLI

npm install -g @angular/cli

- Bước 2 : Tạo dự án bằng angular

ng new angular-bootstrap-demo

- Bước 3 : Nhúng Bootstrap vào trong file index.html 

Chúng ta nhúng đường link bootstrap cdn và jquery vào phần header. Như vậy ta có thể sử dụng được bootstrap.
Đường link đó chúng ta lấy  [tại đây ](https://www.bootstrapcdn.com/)

{% highlight html linenos %}
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>Angular Getting Started</title>
    <base href="/" />

    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <link rel="icon" type="image/x-icon" href="favicon.ico" />
    <link
      href="https://fonts.googleapis.com/icon?family=Material+Icons"
      rel="stylesheet"
    />
    

    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css" integrity="sha384-9aIt2nRpC12Uk9gS9baDl411NQApFmC26EwAOH8WgZl5MYYxFfc+NcPb1dKGj7Sk" crossorigin="anonymous">
	
	<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/js/bootstrap.min.js" integrity="sha384-wfSDF2E50Y2D1uUdj0O3uMBJnjuUD4Ih7YwaYd1iqfktj0Uod8GCExl3Og8ifwB6" crossorigin="anonymous"></script>
	
	<script src="https://code.jquery.com/jquery-3.4.1.slim.min.js" 
	integrity="sha384-J6qa4849blE2+poT4WnyKhv5vZF5SrPo0iEjwBvKU7imGFAV0wwj1yYfoRSJoZ+n" crossorigin="anonymous"></script>
	
	<script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js" integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldlvI9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo" crossorigin="anonymous"></script>

  </head>
  <body>
    <app-root></app-root>
  </body>
</html>
{% endhighlight %}

## **4 Tạo ứng dụng Angular và sử dụng Bootstrap từ npm**

- Bước 1 : Cài đặt Angular CLI

npm install -g @angular/cli

- Bước 2 : Tạo dự án bằng angular

ng new angular-bootstrap-demo

- Bước 3 : Cài đặt bootstrap và jquery bằng lệnh npm

npm install --save bootstrap jquery

- Bước 4 : Nhúng bootstrap và <b>jquery</b>. Mở file angular.json và thêm vào đường dẫn tới file bootstrap và jquery mà mình vừa dùng npm để lôi về dự án

{% highlight json linenos %}
"architect": {
  "build": {
    [...], 
    "styles": [
      "src/styles.css", 
        "node_modules/bootstrap/dist/css/bootstrap.min.css"
      ],
      "scripts": [
        "node_modules/jquery/dist/jquery.min.js",
        "node_modules/bootstrap/dist/js/bootstrap.min.js"
      ]
    },

{% endhighlight %}

## **Tổng kết**

Hầu hết các ứng dụng ngày nay đều sử dụng Bootstrap để làm <b>frontend</b>, tuy nhiên ngoài Boostrap thì mình còn có nhiều framework làm frontend khác nữa. Ưu điểm mạnh nhất các framework này là dể sử dụng và tiết kiệm thời gian để phát triển.


<br>
### Nào chúng ta hãy xem video hướng dẫn dưới đây nhé.
{% include youtubePlayer.html id=page.youtubeId %}
