---
layout: course-css
title: Sử dụng Position 
slug : su-dung-position-trong-css
category: laptrinhweb
tags: [css]
summery: Position 
image: /images/blog/angular.png
description : Sử dụng position trong trong dự án làm web. Hướng dẫn Sử dụng position trong CSS vào dự án web. 
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người cách sử dụng <b>position</b> là như thế nào?

# **1. Position là gì**

Chúng ta sử dụng thuộc tính position để đặt các phẩn tử web ở vị trí mình mong muốn. Trong CSS chúng ta có những vị trí như relative, static, absolute, fix và sticky

# **2. Position static**

Đây là vị trí mặc định khi một thành phần web được tạo ra. Chúng ta khai báo như sau position: static


{% highlight html linenos %}

<!DOCTYPE html>
<html>
<head>
<style>
div.static {
  position: static;
  border: 3px solid #73AD21;
}
</style>
</head>
<body>

<h2>position: static;</h2>

<p>An element with position: static; is not positioned in any special way; it is 
always positioned according to the normal flow of the page:</p>

<div class="static">
  This div element has position: static;
</div>

</body>
</html>

{% endhighlight %}

{:refdef: style="text-align: center;"}
![position1](/images/post/css/position1.png){:class="img-responsive"}
{: refdef}

# **3. Position relative**

Chúng ta sử dụng posistion là relative khi chúng ta muốn phần tử web được tạo ra cách bên trái, phải, trên, dưới so với vị trí mặc định ban đầu. Ví dụ div sau khi được tạo ra nó sẽ cách lề trái 30 px


{% highlight html linenos %}

<!DOCTYPE html>
<html>
<head>
<style>
div.relative {
  position: relative;
  left: 30px;
  border: 3px solid #73AD21;
}
</style>
</head>
<body>

<h2>position: relative;</h2>

<p>An element with position: relative; is positioned relative to its normal position:</p>

<div class="relative">
This div element has position: relative;
</div>

</body>
</html>

{% endhighlight %}

{:refdef: style="text-align: center;"}
![position2](/images/post/css/position2.png){:class="img-responsive"}
{: refdef}

# **4. Position fix**

Chúng ta sử dụng position fix khi chúng ta muốn cố định phần tử trên trang web. Có thể cố định phía trên, dưới, trái hoặc phải


{% highlight html linenos %}

<!DOCTYPE html>
<html>
<head>
<style>
div.fixed {
  position: fixed;
  bottom: 0;
  right: 0;
  width: 300px;
  border: 3px solid #73AD21;
}
</style>
</head>
<body>

<h2>position: fixed;</h2>

<p>An element with position: fixed; is positioned relative to the viewport, which means it always stays in the same place even if the page is scrolled:</p>

<div class="fixed">
This div element has position: fixed;
</div>

</body>
</html>


{% endhighlight %}

{:refdef: style="text-align: center;"}
![position3](/images/post/css/position3.png){:class="img-responsive"}
{: refdef}

# **4. Position absolute**

Chúng ta sử dụng position absolute để canh chỉnh các phẩn tử con bên trong phần tử cha


{% highlight html linenos %}

<!DOCTYPE html>
<html>
<head>
<style>
div.relative {
  position: relative;
  width: 400px;
  height: 200px;
  border: 3px solid #73AD21;
} 

div.absolute {
  position: absolute;
  top: 80px;
  right: 0;
  width: 200px;
  height: 100px;
  border: 3px solid #73AD21;
}
</style>
</head>
<body>

<h2>position: absolute;</h2>

<p>An element with position: absolute; is positioned relative to the nearest positioned ancestor (instead of positioned relative to the viewport, like fixed):</p>

<div class="relative">This div element has position: relative;
  <div class="absolute">This div element has position: absolute;</div>
</div>

</body>
</html>


{% endhighlight %}

{:refdef: style="text-align: center;"}
![position4](/images/post/css/position4.png){:class="img-responsive"}
{: refdef}

# **4. Position sticky**

Chúng ta sử dụng position sticky để cố định phần tử khi người dùng kéo nội dung của trang web thì các phần tử sticky vẫn không di chuyển mà cố định cho người dùng

{% highlight html linenos %}

<!DOCTYPE html>
<html>
<head>
<style>
div.sticky {
  position: -webkit-sticky;
  position: sticky;
  top: 0;
  padding: 5px;
  background-color: #cae8ca;
  border: 2px solid #4CAF50;
}
</style>
</head>
<body>

<p>Try to <b>scroll</b> inside this frame to understand how sticky positioning works.</p>
<p>Note: IE/Edge 15 and earlier versions do not support sticky position.</p>

<div class="sticky">I am sticky!</div>

<div style="padding-bottom:2000px">
  <p>In this example, the sticky element sticks to the top of the page (top: 0), when you reach its scroll position.</p>
  <p>Scroll back up to remove the stickyness.</p>
  <p>Some text to enable scrolling.. Lorem ipsum dolor sit amet, illum definitiones no quo, maluisset concludaturque et eum, altera fabulas ut quo. Atqui causae gloriatur ius te, id agam omnis evertitur eum. Affert laboramus repudiandae nec et. Inciderint efficiantur his ad. Eum no molestiae voluptatibus.</p>
  <p>Some text to enable scrolling.. Lorem ipsum dolor sit amet, illum definitiones no quo, maluisset concludaturque et eum, altera fabulas ut quo. Atqui causae gloriatur ius te, id agam omnis evertitur eum. Affert laboramus repudiandae nec et. Inciderint efficiantur his ad. Eum no molestiae voluptatibus.</p>
</div>

</body>
</html>



{% endhighlight %}

{:refdef: style="text-align: center;"}
![position5](/images/post/css/position5.png){:class="img-responsive"}
{: refdef}

Trong ví dụ trên người dùng dù có kéo thanh scroll bar thì chữ I am sticky vẫn ở trên cùng và cố định cho dù người dùng có kéo thanh cuộn xuống.


