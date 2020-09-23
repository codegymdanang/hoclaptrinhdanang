---
layout: course-css
title: Sử dụng CSS trong HTML  
slug : su-dung-css-trong-html
category: laptrinhweb
tags: [css]
summery: Sử dụng CSS trong HTML  
image: /images/blog/angular.png
description : Sử dụng CSS trong HTML trong dự án làm web. Hướng dẫn Sử dụng CSS trong HTML vào dự án web. 
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người cách sử dụng <b>Sử dụng CSS trong HTML</b> là như thế nào?

# **1. Nhúng CSS vào HTML thông qua thẻ style**

{% highlight html linenos %}

<!DOCTYPE html>
<html>
   <head>
      <style type = "text/css" media = "all">
         body {
            background-color: linen;
         }
         h1 {
            color: maroon;
            margin-left: 40px;
         }
      </style>
   </head>   
   <body>
      <h1>This is a heading</h1>
      <p>This is a paragraph.</p>
   </body>
</html>

{% endhighlight %}

{:refdef: style="text-align: center;"}
![css1](/images/post/css/css1.png){:class="img-responsive"}
{: refdef}

# **2. Nhúng CSS vào HTML trong một hàng**

{% highlight html linenos %}

<!DOCTYPE html>
<html>
   <head>
   </head>

   <body>
      <h1 style = "color:#36C;"> 
         This is inline CSS 
      </h1>
   </body>
</html>

{% endhighlight %}

{:refdef: style="text-align: center;"}
![css2](/images/post/css/css2.png){:class="img-responsive"}
{: refdef}


# **3. Nhúng CSS vào HTML qua file**

Giả sử chúng ta có một file css tên my.css như sau

{% highlight css linenos %}

h1, h2, h3 {
   color: #36C;
   font-weight: normal;
   letter-spacing: .4em;
   margin-bottom: 1em;
   text-transform: lowercase;
}

{% endhighlight %}

Ta sẽ nhúng file my.css này vào trang HTML thông qua thẻ link như sau

{% highlight html linenos %}

<!DOCTYPE html>
<html>
   <head>
      <link type = "text/css" href = "my.css" media = " all" />
   </head>

   <body>
      <h1 style = "color:#36C;"> 
         This is inline CSS 
      </h1>
   </body>
</html>


{% endhighlight %}

- Ngoài cách dùng thẻ link chúng ta có thể sử dụng annotation @import như sau


{% highlight html linenos %}

<!DOCTYPE html>
<html>
   <head>
     @import "my.css";
   </head>

   <body>
      <h1 style = "color:#36C;"> 
         This is inline CSS 
      </h1>
   </body>
</html>


{% endhighlight %}

# **4. Comment chú thích trong CSS**

Chúng ta dùng /* để ghi chú thích các dòng code CSS như sau.


{% highlight html linenos %}

<!DOCTYPE html>
<html>
   <head>
      <style>
         p {
            color: red;
            /* This is a single-line comment */
            text-align: center;
         }
         /* This is a multi-line comment */
      </style>
   </head>

   <body>
      <p>Hello World!</p>
   </body>
</html>

{% endhighlight %}











