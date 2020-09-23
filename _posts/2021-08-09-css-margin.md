---
layout: course-css
title: Sử dụng Margin 
slug : su-dung-margin-trong-css
category: laptrinhweb
tags: [css]
summery: Margin 
image: /images/blog/angular.png
description : Sử dụng margin trong trong dự án làm web. Hướng dẫn Sử dụng margin trong CSS vào dự án web. 
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người cách sử dụng <b>margin</b> là như thế nào?

# **1. Margin là gì**

Chúng ta sử dụng thuộc tính margin để thiết lập khoảng cách giữa các phần tử trong HTML. Margin gồm có các giá trị như margin-bottom canh dưới, margin-top canh trên, margin-left canh trái, và margin-right canh phải


# **2. Thuộc tính Margin**

Ví dụ như anh sẽ thiết lập 4 thuộc tính của margin cho đoạn văn bản như sau.

{% highlight html linenos %}

<html>
   <head>
   </head>
   
   <body>
      <p style = "margin: 15px; border:1px solid black;">
         all four margins will be 15px
      </p>
      
      <p style = "margin:10px 2%; border:1px solid black;">
         top and bottom margin will be 10px, left and right margin will be 2% 
         of the total width of the document.
      </p>
      
      <p style = "margin: 10px 2% -10px; border:1px solid black;">
         top margin will be 10px, left and right margin will be 2% of the 
         total width of the document, bottom margin will be -10px
      </p>
      
      <p style = "margin: 10px 2% -10px auto; border:1px solid black;">
         top margin will be 10px, right margin will be 2% of the total 
         width of the document, bottom margin will be -10px, left margin 
         will be set by the browser
      </p>
   </body>
</html> 
{% endhighlight %}

{:refdef: style="text-align: center;"}
![margin1](/images/post/css/margin1.png){:class="img-responsive"}
{: refdef}

# **2. Thuộc tính Margin bottom**

Sử dụng để canh chỉnh ở phần dưới của phần tử web. Chúng ta có các giá trị là pixel hoặc %

{% highlight html linenos %}

<html>
   <head>
   </head>

   <body>
      <p style = "margin-bottom: 15px; border:1px solid black;">
         This is a paragraph with a specified bottom margin
      </p>
      
      <p style = "margin-bottom: 5%; border:1px solid black;">
         This is another paragraph with a specified bottom margin in percent
      </p>
   </body>
</html> 
{% endhighlight %}

{:refdef: style="text-align: center;"}
![margin2](/images/post/css/margin2.png){:class="img-responsive"}
{: refdef}

# **3. Thuộc tính Margin top**

Sử dụng để canh chỉnh ở phần trên của phần tử web. Chúng ta có các giá trị là pixel hoặc %

{% highlight html linenos %}

<html>
   <head>
   </head>

   <body>
      <p style = "margin-top: 15px; border:1px solid black;">
         This is a paragraph with a specified top margin
      </p>
      
      <p style = "margin-top: 5%; border:1px solid black;">
         This is another paragraph with a specified top margin in percent
      </p>
   </body>
</html>

{% endhighlight %}

{:refdef: style="text-align: center;"}
![margin3](/images/post/css/margin3.png){:class="img-responsive"}
{: refdef}

# **4. Thuộc tính Margin left**

Sử dụng để canh chỉnh ở phần bên trái của phần tử web. Chúng ta có các giá trị là pixel hoặc %

{% highlight html linenos %}

<html>
   <head>
   </head>

   <body>
      <p style = "margin-left: 15px; border:1px solid black;">
         This is a paragraph with a specified left margin
      </p>
      
      <p style = "margin-left: 5%; border:1px solid black;">
         This is another paragraph with a specified top margin in percent
      </p>
   </body>
</html> 

{% endhighlight %}

{:refdef: style="text-align: center;"}
![margin4](/images/post/css/margin4.png){:class="img-responsive"}
{: refdef}

# **5. Thuộc tính Margin right**

Sử dụng để canh chỉnh ở phần bên phải của phần tử web. Chúng ta có các giá trị là pixel hoặc %

{% highlight html linenos %}

<html>
   <head>
   </head>
   
   <body>
      <p style = "margin-right: 15px; border:1px solid black;">
         This is a paragraph with a specified right margin
      </p>
      <p style = "margin-right: 5%; border:1px solid black;">
         This is another paragraph with a specified right margin in percent
      </p>
   </body>
</html> 

{% endhighlight %}

{:refdef: style="text-align: center;"}
![margin5](/images/post/css/margin5.png){:class="img-responsive"}
{: refdef}













