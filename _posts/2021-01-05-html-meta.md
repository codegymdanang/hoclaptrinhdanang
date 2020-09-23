---
layout: course-html
title: Thẻ Meta   
slug : the-meta-html
category: laptrinhweb
tags: [html]
summery: Thẻ Meta   
image: /images/blog/angular.png
description : Sử dụng các thẻ Meta từ trong HTML trong dự án làm web. Hướng dẫn sử dụng thẻ Meta trong  HTML vào dự án web. 
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người cách sử dụng thẻ <b>thẻ Meta </b> là như thế nào?

# **1. Thẻ meta**

Chúng ta sử dụng thẻ meta để thêm các thông tin mô tả cho trang web. Thông thường các trang web sử dụng thẻ meta để tăng thứ hạng SEO trong google. Nó là một tiêu chí để google có thể hiểu rõ về website của mình.

Thẻ meta được khai báo trong thẻ head. Nó gồm có các thuộc tính name, content, schema và http-equiv.

# **2. Mô tả từ khoá chính về trang web**

Chúng ta sử dụng thẻ meta để chỉ ra những từ khoá nào là quan trọng mà website chúng ta đang làm về nó. Điều này giúp google có thể đánh index lại. Chúng ta sử dụng thuộc tính keywork như sau.

{% highlight html linenos %}

<!DOCTYPE html>
<html>
   
   <head>
      <title>Meta Tags Example</title>
      <meta name = "keywords" content = "HTML, Meta Tags, Metadata" />
   </head>
   
   <body>
      <p>Hello HTML5!</p>
   </body>
   
</html>

{% endhighlight %} 

- content : chính là các từ khoá mà website chúng ta đang làm. Ví dụ như làm về các website du lịch thì content sẽ chứa đựng các từ khoá về du lịch.

# **2. Mô tả về nội dung trang web**

Chúng ta dùng description để mô tả nội dung website mình làm về cái gì.

{% highlight html linenos %}

<!DOCTYPE html>
<html>

   <head>
      <title>Meta Tags Example</title>
      <meta name = "keywords" content = "HTML, Meta Tags, Metadata" />
      <meta name = "description" content = "Learning about Meta Tags." />
   </head>
   
   <body>
      <p>Hello HTML5!</p>
   </body>
   
</html>

{% endhighlight %} 

# **3. Mô tả thời gian cập nhật trang web**

Chúng ta dùng revised để mô tả thời gian nội dung website được cập nhật.

{% highlight html linenos %}

<!DOCTYPE html>
<html>

   <head>
      <title>Meta Tags Example</title>
      <meta name = "keywords" content = "HTML, Meta Tags, Metadata" />
      <meta name = "description" content = "Learning about Meta Tags." />
      <meta name = "revised" content = "Tutorialspoint, 3/7/2014" />
   </head>
   
   <body>
      <p>Hello HTML5!</p>
   </body>
   
</html>

{% endhighlight %}

# **4. Làm mới lại trang web**

Chúng ta có thể cấu hình để trang web tự động refresh (làm mới) sau một khoản thời gian bằng thuộc tính refresh như sau.

{% highlight html linenos %}

<!DOCTYPE html>
<html>

   <head>
      <title>Meta Tags Example</title>
      <meta name = "keywords" content = "HTML, Meta Tags, Metadata" />
      <meta name = "description" content = "Learning about Meta Tags." />
      <meta name = "revised" content = "Tutorialspoint, 3/7/2014" />
      <meta http-equiv = "refresh" content = "5" />
   </head>
   
   <body>
      <p>Hello HTML5!</p>
   </body>
   
</html>

{% endhighlight %}


# **5. Chuyển hướng trang tới một trang web khác**

Chúng ta có thể thiết lập trang web sau một khoản thời gian cố định nó sẽ chuyển qua một trang web khác bằng cách thêm thuộc tính content và đường link trang web khác như sau

{% highlight html linenos %}

<!DOCTYPE html>
<html>

   <head>
      <title>Meta Tags Example</title>
      <meta name = "keywords" content = "HTML, Meta Tags, Metadata" />
      <meta name = "description" content = "Learning about Meta Tags." />
      <meta name = "revised" content = "Tutorialspoint, 3/7/2014" />
      <meta http-equiv = "refresh" content = "5; url = http://www.tutorialspoint.com" />
   </head>
   
   <body>
      <p>Hello HTML5!</p>
   </body>
   
</html>

{% endhighlight %}


# **6. Thêm author cho website**

Chúng ta sử dụng thuộc tính author để thêm tên mà người làm ra trang web như sau

{% highlight html linenos %}

<!DOCTYPE html>
<html>

   <head>
      <title>Meta Tags Example</title>
      <meta name = "keywords" content = "HTML, Meta Tags, Metadata" />
      <meta name = "description" content = "Learning about Meta Tags." />
      <meta name = "author" content = "Mahnaz Mohtashim" />
   </head>
   
   <body>
      <p>Hello HTML5!</p>
   </body>
   
</html>

{% endhighlight %}

# **7. Thiết lập mã hoá ký tự cho website**

Chúng ta có thể sử dụng bảng mã UTF8 để viết tiếng Việt hoặc đối với các ngôn ngữ khác như Campuchia hay Thailand thì dùng bảng chữ cái khác. Bằng cách set thuộc tính charset như sau. Trong ví dụ này ta dùng UTF-8

{% highlight html linenos %}

<!DOCTYPE html>
<html>

   <head>
      <title>Meta Tags Example</title>
      <meta name = "keywords" content = "HTML, Meta Tags, Metadata" />
      <meta name = "description" content = "Learning about Meta Tags." />
      <meta name = "author" content = "Mahnaz Mohtashim" />
      <meta http-equiv = "Content-Type" content = "text/html; charset = UTF-8" />
   </head>
   
   <body>
      <p>Hello HTML5!</p>
   </body>
   
</html>

{% endhighlight %}

- Ví dụ như viết chữ Trung Quốc thì ta dùng charset Big5 như sau

{% highlight html linenos %}

<!DOCTYPE html>
<html>

   <head>
      <title>Meta Tags Example</title>
      <meta name = "keywords" content = "HTML, Meta Tags, Metadata" />
      <meta name = "description" content = "Learning about Meta Tags." />
      <meta name = "author" content = "Mahnaz Mohtashim" />
      <meta http-equiv = "Content-Type" content = "text/html; charset = Big5" />
   </head>
   
   <body>
      <p>Hello HTML5!</p>
   </body>
   
</html>

{% endhighlight %}









