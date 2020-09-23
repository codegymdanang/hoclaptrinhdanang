---
layout: course-css
title: Sử dụng background 
slug : su-dung-background-trong-css
category: laptrinhweb
tags: [css]
summery: Background  
image: /images/blog/angular.png
description : Sử dụng background trong trong dự án làm web. Hướng dẫn Sử dụng background trong CSS vào dự án web. 
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người cách sử dụng <b>background</b> là như thế nào?

# **1. Background về màu sắc**

Chúng ta sử dụng background-color để làm màu nền.

{% highlight html linenos %}

<html>
   <head>
   </head>

   <body>
      <p style = "background-color:yellow;">
         This text has a yellow background color.
      </p>
   </body>
</html> 

{% endhighlight %}

{:refdef: style="text-align: center;"}
![background1](/images/post/css/background1.png){:class="img-responsive"}
{: refdef}


# **2. Background là ảnh**

Chúng ta có thể sử dụng ảnh để làm background bằng cách sử dụng thuột tính background-image

{% highlight html linenos %}

<html>
   <head>
      <style>
         body  {
            background-image: url("/css/images/css.jpg");
            background-color: #cccccc;
         }
      </style>
   </head>
   
   <body>
      <h1>Hello World!</h1>
   </body>
<html>
{% endhighlight %}

{:refdef: style="text-align: center;"}
![background2](/images/post/css/background2.png){:class="img-responsive"}
{: refdef}


# **3. Lặp lại Background**

Nếu ảnh trong background nhở hơn kích thướt của website. Thì ta có thể lăp lại (repeat) cái ảnh background theo chiều ngang hoặc dọc.

Ví dụ để lăp lại hình ảnh ta sử dụng thuộc tính background-repeat

{% highlight html linenos %}

<html>
   <head>
      <style>
         body {
            background-image: url("/css/images/css.jpg");
            background-repeat: repeat;
         }
      </style>
   </head>

   <body>
      <p>Le Vu Nguyen Blog</p>
   </body>
</html>

{% endhighlight %}

{:refdef: style="text-align: center;"}
![background3](/images/post/css/background3.png){:class="img-responsive"}
{: refdef}

- Nếu muốn lặp lại theo chiều dọc ta sử dụng thuộc tính background-repeat: repeat-y

{% highlight html linenos %}

<html>
   <head>
      <style>
         body {
            background-image: url("/css/images/css.jpg");
            background-repeat: repeat-y;
         }
      </style>
   </head>

   <body>
      <p>Le Vu Nguyen</p>
   </body>
</html>

{% endhighlight %}

{:refdef: style="text-align: center;"}
![background4](/images/post/css/background4.png){:class="img-responsive"}
{: refdef}

- Nếu muốn lặp lại theo chiều ngang ta sử dụng thuộc tính background-repeat: repeat-x

{% highlight html linenos %}

<html>
   <head>
      <style>
         body {
            background-image: url("/css/images/css.jpg");
            background-repeat: repeat-x;
         }
      </style>
   </head>
   
   <body>
      <p>Le Vu Nguyen</p>
   </body>
</html>

{% endhighlight %}

{:refdef: style="text-align: center;"}
![background5](/images/post/css/background5.png){:class="img-responsive"}
{: refdef}

# **4. Canh chỉnh vị trí Background**

Ví dụ như anh muốn canh vị trí background ảnh cách bên lề trái 100 pixels thì anh sử dụng thuộc tính background-position

{% highlight html linenos %}

<html>
   <head>
      <style>
         body {
            background-image: url("/css/images/css.jpg");
            background-position:100px;
         }
      </style>
   </head>

   <body>
      <p>Tutorials point</p>
   </body>
</html>

{% endhighlight %}

- Ví dụ như anh muốn canh ảnh background bên trái 100 pixels và bên dưới 200 pixels thì anh làm như sau

{% highlight html linenos %}

<html>
   <head>
      <style>
         body {
            background-image: url("/css/images/css.jpg");
            background-position:100px 200px;
         }
      </style>
   </head>

   <body>
      <p>Tutorials point</p>
   </body>
</html>

{% endhighlight %}


# **5. Fix cứng vị trí Background**

Trong trường hợp trang web có nội dung dài thì sẽ xuất hiện thanh cuộn bên tay phải để mình có thể kéo lên kéo xuống xem nội dung. Nhưng anh mong muốn nội dụng có thể chạy lên chạy xuống nhưng ảnh background vẫn giữa nguyên vị trí. Lúc này anh muốn fix cứng vị ví của ảnh cho dù người dùng có kéo lên hoặc xuống. Anh sẽ sử dụng thuộc tính background-attachment như sau

{% highlight html linenos %}

<!DOCTYPE html>
<html>
   <head>
      <style>
         body {
            background-image: url('/css/images/css.jpg');
            background-repeat: no-repeat;
            background-attachment: fixed;
         }
      </style>
   </head>

   <body>
      <p>The background-image is fixed. Try to scroll down the page.</p>
      <p>The background-image is fixed. Try to scroll down the page.</p>
      <p>The background-image is fixed. Try to scroll down the page.</p>
      <p>The background-image is fixed. Try to scroll down the page.</p>
      <p>The background-image is fixed. Try to scroll down the page.</p>
      <p>The background-image is fixed. Try to scroll down the page.</p>
      <p>The background-image is fixed. Try to scroll down the page.</p>
      <p>The background-image is fixed. Try to scroll down the page.</p>
      <p>The background-image is fixed. Try to scroll down the page.</p>
   </body>
</html>

{% endhighlight %}

Trường hợp ngược lại nếu anh muốn background cũng cuộn theo nếu người dùng kéo thanh cuộn thì anh sử dụng như sau

{% highlight html linenos %}

<!DOCTYPE html>
<html>
   <head>
      <style>
         body {
            background-image: url('/css/images/css.jpg');
            background-repeat: no-repeat;
            background-attachment: fixed;
            background-attachment:scroll;
         }
      </style>
   </head>

   <body>
      <p>The background-image is fixed. Try to scroll down the page.</p>
      <p>The background-image is fixed. Try to scroll down the page.</p>
      <p>The background-image is fixed. Try to scroll down the page.</p>
      <p>The background-image is fixed. Try to scroll down the page.</p>
      <p>The background-image is fixed. Try to scroll down the page.</p>
      <p>The background-image is fixed. Try to scroll down the page.</p>
      <p>The background-image is fixed. Try to scroll down the page.</p>
      <p>The background-image is fixed. Try to scroll down the page.</p>
      <p>The background-image is fixed. Try to scroll down the page.</p>
   </body>
</html>

{% endhighlight %}









