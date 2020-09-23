---
layout: course-bootstrap
title: Sử dụng Util trong boostrap 
slug : bootstrap-util
category: laptrinhweb
tags: [bootstrap]
summery: Util
image:
description : Giới thiệu về Util, hướng dẫn cách sử dụng Util trong lập trình web.
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>Util</b> là gì? Các sử dụng nó trong lập trình website. 

# **1. Util trong Bootstrap 4**

Boostrap 4 đã xây dựng sẳn một số thư viện và tính năng để trang trí web và các thành phần trong web. Sau đây là những tính năng có sẳn

# **2. Border trong Bootstrap 4**

Sử dụng class border để thêm hoặc xoá một border của một thành phần web

<br>
{% highlight html  linenos %}

 <span class="border"></span>
<span class="border border-0"></span>
<span class="border border-top-0"></span>
<span class="border border-right-0"></span>
<span class="border border-bottom-0"></span>
<span class="border border-left-0"></span>

{% endhighlight %}


# **3. Thêm màu sắc cho Border trong Bootstrap 4**

<br>
{% highlight html  linenos %}

<span class="border border-primary"></span>
<span class="border border-secondary"></span>
<span class="border border-success"></span>
<span class="border border-danger"></span>
<span class="border border-warning"></span>
<span class="border border-info"></span>
<span class="border border-light"></span>
<span class="border border-dark"></span>
<span class="border border-white"></span>

{% endhighlight %}

# **4. Border có góc viền tròn trong Bootstrap 4**

<br>
{% highlight html  linenos %}


<span class="rounded-sm"></span>
<span class="rounded"></span>
<span class="rounded-lg"></span>
<span class="rounded-top"></span>
<span class="rounded-right"></span>
<span class="rounded-bottom"></span>
<span class="rounded-left"></span>
<span class="rounded-circle"></span>
<span class="rounded-0"></span>

{% endhighlight %}

{:refdef: style="text-align: center;"}
![borderround](/images/post/boostrap/borderround.png){:class="img-responsive"}
{: refdef}

# **5. Float Bootstrap 4**

Chúng ta có thể sử dụng float right bằng class .float-right, hay float left bằng class .float-left. Hoặc chúng ta muốn xoá  tính năng float đi thì dùng class  .clearfix

<br>
{% highlight html  linenos %}

<div class="clearfix">
  <span class="float-left">Float left</span>
  <span class="float-right">Float right</span>
</div>

{% endhighlight %}

# **6. Canh giữa trong Bootstrap 4**

Chúng ta sử dụng class .mx-auto để canh giữa cho các phần tử.

<br>
{% highlight html  linenos %}

 <div class="mx-auto bg-warning" style="width:150px">Centered</div>

{% endhighlight %}

# **7. Thiết lập độ rộng của các phần tử trong Bootstrap 4** 

Chúng ta có thể sử dụng class w-* . Trong đó * là phần trăm độ rộng mà phần tử web sẽ chiếm

<br>
{% highlight html  linenos %}

<div class="w-25 bg-warning">Width 25%</div>
<div class="w-50 bg-warning">Width 50%</div>
<div class="w-75 bg-warning">Width 75%</div>
<div class="w-100 bg-warning">Width 100%</div>
<div class="mw-100 bg-warning">Max Width 100%</div>

{% endhighlight %}

# **8. Thiết lập độ cao của các phần tử trong Bootstrap 4** 

Tương tự như thiết lập độ rộng ta cũng có thể thiết lập độ cao cho các phần tử bằng class h-* . Trong đó * là phần trăm độ rộng sẽ chiếm.

<br>
{% highlight html  linenos %}

<div style="height:200px;background-color:#ddd">
  <div class="h-25 bg-warning">Height 25%</div>
  <div class="h-50 bg-warning">Height 50%</div>
  <div class="h-75 bg-warning">Height 75%</div>
  <div class="h-100 bg-warning">Height 100%</div>
  <div class="mh-100 bg-warning" style="height:500px">Max Height 100%</div>
</div>

{% endhighlight %}

# **9. Tạo hiệu ứng bóng đổ** 

<br>
{% highlight html  linenos %}

<div class="shadow-none p-4 mb-4 bg-light">No shadow</div>
<div class="shadow-sm p-4 mb-4 bg-white">Small shadow</div>
<div class="shadow p-4 mb-4 bg-white">Default shadow</div>
<div class="shadow-lg p-4 mb-4 bg-white">Large shadow</div>

{% endhighlight %}

# **10. Iframe Responsive** 

Khi ta nhúng video và website ở một nguồn khác vào trang web mình. Mà mình muốn chúng responsive giống như trang web mình thì mình thêm class embed-responsive-item ở div cha và div con nơi chứa iframe mình thêm class .embed-responsive như sau

<br>
{% highlight html  linenos %}

<!-- 21:9 aspect ratio -->
<div class="embed-responsive embed-responsive-21by9">
  <iframe class="embed-responsive-item" src="..."></iframe>
</div>

<!-- 16:9 aspect ratio -->
<div class="embed-responsive embed-responsive-16by9">
  <iframe class="embed-responsive-item" src="..."></iframe>
</div>

<!-- 4:3 aspect ratio -->
<div class="embed-responsive embed-responsive-4by3">
  <iframe class="embed-responsive-item" src="..."></iframe>
</div>

<!-- 1:1 aspect ratio -->
<div class="embed-responsive embed-responsive-1by1">
  <iframe class="embed-responsive-item" src="..."></iframe>
</div>

{% endhighlight %}

# **11. Ẩn hiện các thành phần web**

Chúng ta có thể ẩn hoặc hiện các thành phần của web bằng cách sử dụng class .visible hoặc .invisible 

<br>
{% highlight html  linenos %}

<div class="visible">I am visible</div>
<div class="invisible">I am invisible</div>

{% endhighlight %}

# **12. Position Vị trí**

- Để đặt một phần tử cố định ở trên cùng của trang thì sử dụng class .fixed-top.

<br>
{% highlight html  linenos %}

 <nav class="navbar navbar-expand-sm bg-dark navbar-dark fixed-top">
  ...
</nav> 

{% endhighlight %}

- Để làm một phần tử cố định ở dưới cùng của trang thì dùng class .fixed-bottom

<br>
{% highlight html  linenos %}

 <nav class="navbar navbar-expand-sm bg-dark navbar-dark fixed-bottom">
  ...
</nav> 
{% endhighlight %}

- Để làm sticky chúng ta sử dụng class .sticky-top

<br>
{% highlight html  linenos %}


 <nav class="navbar navbar-expand-sm bg-dark navbar-dark sticky-top">
  ...
</nav> 

{% endhighlight %}

# **13. Close Icon**

Chúng ta có thể thêm nút có biểu tượng close (x) bằng class .close

<br>
{% highlight html  linenos %}

 <button type="button" class="close">&times;</button>
{% endhighlight %}


