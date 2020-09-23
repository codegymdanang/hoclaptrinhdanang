---
layout: course-bootstrap
title: Sử dụng màu trong boostrap 
slug : bootstrap-color
category: laptrinhweb
tags: [bootstrap]
summery: Màu sắc
image:
description : Giới thiệu về màu sắc, hướng dẫn cách sử dụng màu sắc trong lập trình web.
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>màu sắc</b> là gì? Các sử dụng nó trong lập trình website. 

# **1. Màu sắc cho Text trong Bootstrap 4**

Trong bootstrap có những class sau được sử dụng để làm màu sắc cho các chữ (text) như là .text-muted, .text-primary, .text-success, .text-info, .text-warning, .text-danger, .text-secondary, .text-white, .text-dark, .text-body (default body color/often black) and .text-light

Ví dụ như ta có các màu sau.

<br>
{% highlight html  linenos %}

<h2>Contextual Colors</h2>
  <p>Use the contextual classes to provide "meaning through colors":</p>
  <p class="text-muted">This text is muted.</p>
  <p class="text-primary">This text is important.</p>
  <p class="text-success">This text indicates success.</p>
  <p class="text-info">This text represents some information.</p>
  <p class="text-warning">This text represents a warning.</p>
  <p class="text-danger">This text represents danger.</p>
  <p class="text-secondary">Secondary text.</p>
  <p class="text-dark">This text is dark grey.</p>
  <p class="text-body">Default body color (often black).</p>
  <p class="text-light">This text is light grey (on white background).</p>
  <p class="text-white">This text is white (on white background).</p>

{% endhighlight %}


{:refdef: style="text-align: center;"}
![Color](/images/post/boostrap/color.png){:class="img-responsive"}
{: refdef}

# **2. Màu sắc cho Background trong Bootstrap 4**

Để tạo màu cho backgroup chúng ta có các màu sắc sau đây : .bg-primary, .bg-success, .bg-info, .bg-warning, .bg-danger, .bg-secondary, .bg-dark and .bg-light. Cái này chỉ dùng cho màu background không sử dụng cho text được.

<br>
{% highlight html  linenos %}

<div class="container">
  <h2>Contextual Backgrounds</h2>
  <p>Use the contextual background classes to provide "meaning through colors".</p>
  <p>Note that you can also add a .text-* class if you want a different text color:</p>
  <p class="bg-primary text-white">This text is important.</p>
  <p class="bg-success text-white">This text indicates success.</p>
  <p class="bg-info text-white">This text represents some information.</p>
  <p class="bg-warning text-white">This text represents a warning.</p>
  <p class="bg-danger text-white">This text represents danger.</p>
  <p class="bg-secondary text-white">Secondary background color.</p>
  <p class="bg-dark text-white">Dark grey background color.</p>
  <p class="bg-light text-dark">Light grey background color.</p>
</div>

{% endhighlight %}


{:refdef: style="text-align: center;"}
![Background Color](/images/post/boostrap/bgcolor.png){:class="img-responsive"}
{: refdef}
