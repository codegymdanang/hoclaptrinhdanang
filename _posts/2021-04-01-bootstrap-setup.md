---
layout: course-bootstrap
title: Cài đặt bootstrap
slug : cai-dat-bootstrap
category: laptrinhweb
tags: [bootstrap]
summery: Cài đặt bootstrap
image:
description : Giới thiệu về bootstrap, hướng dẫn cách sử dụng bootstrap trong lập trình web.
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>Bootstap</b> là gì? Các sử dụng nó trong lập trình website 

# **1. Boostrap là gì**

Boostrap là một framework giups chúng ta xây dựng website một cách nhanh chóng và dể dàng. Trong framework bootstrap đã xây dựng sẳn các thiết kế và các template cho form, button, tables, navigation, modal bằng HTML và CSS. Chúng ta chỉ việc sử dụng và không cần mất thời gian để thiết kế. Ngoài ra Bootstrap còn cung cấp cho chúng ta những thư viện Javascript hỗ trợ cho việc làm hiệu ứng trên website. Sử dụng Boostrap sẽ giúp website trở nên responsive, có nghĩa là website sẽ được hiển thị trên nhiều nền tảng khác nhau như điện thoại, máy tính, tivi 

# **2. Tại sao lại dùng Boostrap**

Hầu hết 70% các lập trình viên đều sử dụng Bootstrap để làm web vì nó có các ưu điểm sau

- Dể sử dụng : Chỉ cần có nền tảng HTML và CSS mọi người có thể sử dụng thành thạo Bootstrap

- Responsive : Chúng ta không cần mất thời gian để canh chỉnh các thành phần trên web để chúng hiện thị trên đa nền tảng (web,mobile,table)

- Tương thích các trình duyệt : Boostrap tương thích với hầu hết các trình duyệt Chrome, Firefox, Safari, và Opera.

# **3. Làm sao nhúng Boostrap vào website**

Có 2 cách chúng ta có thể nhúng Boostrap vào website và sử dụng

- Chúng ta có thể lấy bootstrap thừ CDN
<br>
{% highlight html  linenos %}

 <!-- Latest compiled and minified CSS -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">

<!-- jQuery library -->
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>

<!-- Popper JS -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.16.0/umd/popper.min.js"></script>

<!-- Latest compiled JavaScript -->
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script> 

{% endhighlight %}

Khi sử dụng CDN thì khi trang web mình load lên nó sẽ lên mạng lấy file boostrap.min.js về. Chúng ta không cần phải download nguyên framework bootstrap về dự án

- Download framework Bookstrap từ getbootstrap.com

Chúng ta lên website getbootstrap sau đó download nguyên bộ boostrap về folder của dự án và dùng

# **4. Tạo website với Bootstrap**

- Bước 1 : tạo trang HTML5 Doctype

Boostrap sử dụng HTML elements và các thuộc tính Css nên yêu cầu HTML5 doctype ở đầu file html
<br>
{% highlight html  linenos %}

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
  </head>
</html>

{% endhighlight %}

- Bước 2 : Cấu hình responsive trên điện thoại

Hiện nay số lượng người dùng điện thoại là rất lớn, nên website của mình cũng phải hiển thị được trên điện thoại. Chính vì vậy khi làm một website mình phải ưu tiên nó phải hiện thị trên được thoại trước.

Chúng ta thêm thẻ meta trong the head để cấu hình

<br>
{% highlight html  linenos %}

<meta name="viewport" content="width=device-width, initial-scale=1">

{% endhighlight %}

+ Thẻ viewport cấu hình cho trang web có thể hiển thị tương thích với các thiết bị khác nhau như mobile, máy desktop, máy table hoặc tivi.

+ Thuộc tính width=device-width nói trang web sẽ có  chiều rộng của mình bằng chiều rộng màn hình của thiết bị.

+ Thuộc tính initial-scale=1.0 dùng để cấu hình mức zoom ban đầu khi trang web được load lên.

- Bước 3 : Thêm framework bootstrap vào website

<br>
{% highlight html  linenos %}

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
  </head>
   <!-- Latest compiled and minified CSS -->
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">

    <!-- jQuery library -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>

    <!-- Popper JS -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.16.0/umd/popper.min.js"></script>

    <!-- Latest compiled JavaScript -->
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script> 

    <body>

    </body>

</html>

{% endhighlight %}

- Bước 4 : Xây dựng trang web

Tiếp đến chúng ta sẽ xây dựng các thành phần của website trong thẻ body. Trong các chủ đề tiếp theo anh sẽ hướng dẫn mọi người cách xây dựng các thành phần





