---
layout: course-bootstrap
title: Sử dụng Nav trong boostrap 
slug : bootstrap-nav
category: laptrinhweb
tags: [bootstrap]
summery: Nav
image:
description : Giới thiệu về nav, hướng dẫn cách sử dụng nav trong lập trình web.
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>nav</b> là gì? Các sử dụng nó trong lập trình website. 

# **1. Nav Menu nằm ngang trong Bootstrap 4**

Chúng ta muốn làm menu cho website thì có thể sử dụng class .nav trong các thẻ ul. Và theo sau đó là các class .nav-item trong các thẻ li. Nếu trong menu có thêm link tới một website khác thì dùng class .nav-link

{:refdef: style="text-align: center;"}
![nav1](/images/post/boostrap/nav1.png){:class="img-responsive"}
{: refdef}

<br>
{% highlight html  linenos %}

 <ul class="nav">
  <li class="nav-item">
    <a class="nav-link" href="#">Link</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" href="#">Link</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" href="#">Link</a>
  </li>
  <li class="nav-item">
    <a class="nav-link disabled" href="#">Disabled</a>
  </li>
</ul> 

{% endhighlight %}

- Để canh giữa cho các Nav thì chúng ta sử dụng class .justify-content-center lúc này thanh menu sẽ nằm giữa màn hình. Nếu muốn thanh menu mà nằm bên trái thì dùng class .justify-content-end

<br>
{% highlight html  linenos %}

<!-- Centered nav -->
<ul class="nav justify-content-center">

<!-- Right-aligned nav -->
<ul class="nav justify-content-end">

{% endhighlight %}


# **2. Nav Menu nằm dọc trong Bootstrap 4**

Chúng ta có thể làm các thanh menu nằm dọc bằng cách thêm class là .flex-column .

{:refdef: style="text-align: center;"}
![nav2](/images/post/boostrap/nav2.png){:class="img-responsive"}
{: refdef}

<br>
{% highlight html  linenos %}

 <ul class="nav flex-column">

{% endhighlight %}

# **3. Tab trong Bootstrap 4**

Chúng ta sử dụng .nav-tab và .active để tạo các tab.

{:refdef: style="text-align: center;"}
![nav3](/images/post/boostrap/nav3.png){:class="img-responsive"}
{: refdef}

<br>
{% highlight html  linenos %}

  <ul class="nav nav-tabs">
  <li class="nav-item">
    <a class="nav-link active" href="#">Active</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" href="#">Link</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" href="#">Link</a>
  </li>
  <li class="nav-item">
    <a class="nav-link disabled" href="#">Disabled</a>
  </li>
</ul> 

{% endhighlight %}

# **4. Tab Pills trong Bootstrap 4**

Chúng ta sử dụng .nav-pills để có thể làm toggle các 

{:refdef: style="text-align: center;"}
![nav4](/images/post/boostrap/nav4.png){:class="img-responsive"}
{: refdef}

<br>
{% highlight html  linenos %}

  <ul class="nav nav-pills">
  <li class="nav-item">
    <a class="nav-link active" href="#">Active</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" href="#">Link</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" href="#">Link</a>
  </li>
  <li class="nav-item">
    <a class="nav-link disabled" href="#">Disabled</a>
  </li>
</ul> 

{% endhighlight %}

# **5. Dynamic tab trong Bootstrap 4**

Chúng ta sử dụng data-toggle="table", .tab-pane và .tab-content để làm Dynamic Tab như sau.

{:refdef: style="text-align: center;"}
![nav5](/images/post/boostrap/nav5.png){:class="img-responsive"}
{: refdef}

<br>
{% highlight html  linenos %}

  <!-- Nav tabs -->
<ul class="nav nav-tabs">
  <li class="nav-item">
    <a class="nav-link active" data-toggle="tab" href="#home">Home</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" data-toggle="tab" href="#menu1">Menu 1</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" data-toggle="tab" href="#menu2">Menu 2</a>
  </li>
</ul>

<!-- Tab panes -->
<div class="tab-content">
  <div class="tab-pane container active" id="home">...</div>
  <div class="tab-pane container fade" id="menu1">...</div>
  <div class="tab-pane container fade" id="menu2">...</div>
</div>

{% endhighlight %}








