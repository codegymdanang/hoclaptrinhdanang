---
layout: course-bootstrap
title: Sử dụng button trong boostrap 
slug : bootstrap-button
category: laptrinhweb
tags: [bootstrap]
summery: Button
image:
description : Giới thiệu về button, hướng dẫn cách sử dụng button trong lập trình web.
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>button</b> là gì? Các sử dụng nó trong lập trình website. 

# **1. Button  trong Bootstrap 4**

{:refdef: style="text-align: center;"}
![button1](/images/post/boostrap/button1.png){:class="img-responsive"}
{: refdef}

<br>
{% highlight html  linenos %}

<button type="button" class="btn">Basic</button>
<button type="button" class="btn btn-primary">Primary</button>
<button type="button" class="btn btn-secondary">Secondary</button>
<button type="button" class="btn btn-success">Success</button>
<button type="button" class="btn btn-info">Info</button>
<button type="button" class="btn btn-warning">Warning</button>
<button type="button" class="btn btn-danger">Danger</button>
<button type="button" class="btn btn-dark">Dark</button>
<button type="button" class="btn btn-light">Light</button>
<button type="button" class="btn btn-link">Link</button> 


{% endhighlight %}

# **2. Button border  trong Bootstrap 4**

{:refdef: style="text-align: center;"}
![button2](/images/post/boostrap/button2.png){:class="img-responsive"}
{: refdef}

<br>
{% highlight html  linenos %}

<button type="button" class="btn btn-outline-primary">Primary</button>
<button type="button" class="btn btn-outline-secondary">Secondary</button>
<button type="button" class="btn btn-outline-success">Success</button>
<button type="button" class="btn btn-outline-info">Info</button>
<button type="button" class="btn btn-outline-warning">Warning</button>
<button type="button" class="btn btn-outline-danger">Danger</button>
<button type="button" class="btn btn-outline-dark">Dark</button>
<button type="button" class="btn btn-outline-light text-dark">Light</button>

{% endhighlight %}

# **3. Kích thướt Button trong Bootstrap 4**

Chúng ta sử dụng class .bnt-lg để tạo cho kích thướt button to nhất, btn-sm cho button có kích thướt nhỏ nhất. Nếu như không dùng 2 class này thì button sẽ lấy kích thướt mặc định


{:refdef: style="text-align: center;"}
![button3](/images/post/boostrap/button3.png){:class="img-responsive"}
{: refdef}

<br>
{% highlight html  linenos %}

<button type="button" class="btn btn-primary btn-lg">Large</button>
<button type="button" class="btn btn-primary">Default</button>
<button type="button" class="btn btn-primary btn-sm">Small</button>

{% endhighlight %}

# **4. Kích thướt Button dài bằng màn hình**

Nếu như ta muốn button có kích thướt chiều dài bằng màn hình thì dùng class .btn-block

<br>
{% highlight html  linenos %}

 <button type="button" class="btn btn-primary btn-block">Full-Width Button</button> 

{% endhighlight %}

# **5. Active và Disable Button**

Chúng ta sử dụng class .active hoặc thuộc tính disable để cho người dùng có thể click hoặc không click được button.

<br>
{% highlight html  linenos %}

<button type="button" class="btn btn-primary active">Active Primary</button>
<button type="button" class="btn btn-primary" disabled>Disabled Primary</button>
<a href="#" class="btn btn-primary disabled">Disabled Link</a> 
{% endhighlight %}


# **6. Nhóm các Button lại với nhau**

Chúng ta có thể nhóm các button lại với nhau trên cùng 1 hàng

{:refdef: style="text-align: center;"}
![button4](/images/post/boostrap/button4.png){:class="img-responsive"}
{: refdef}

<br>
{% highlight html  linenos %}

<div class="btn-group">
  <button type="button" class="btn btn-primary">Apple</button>
  <button type="button" class="btn btn-primary">Samsung</button>
  <button type="button" class="btn btn-primary">Sony</button>
</div> 

{% endhighlight %}

# **7. Nhóm các Button cùng kích thướt lại với nhau**

Chúng ta có thể nhóm các button lại với nhau trên cùng kích thướt

{:refdef: style="text-align: center;"}
![button5](/images/post/boostrap/button5.png){:class="img-responsive"}
{: refdef}

<br>
{% highlight html  linenos %}

  <div class="btn-group btn-group-lg">
  <button type="button" class="btn btn-primary">Apple</button>
  <button type="button" class="btn btn-primary">Samsung</button>
  <button type="button" class="btn btn-primary">Sony</button>
</div> 

{% endhighlight %}

# **8. Sắp xếp  các Button theo hàng dọc**

Chúng ta sử dụng class .btn-group-vertical để sắp xếp các button theo chiều dọc

<br>
{% highlight html  linenos %}

 <div class="btn-group-vertical">
  <button type="button" class="btn btn-primary">Apple</button>
  <button type="button" class="btn btn-primary">Samsung</button>
  <button type="button" class="btn btn-primary">Sony</button>
</div> 

{% endhighlight %}

# **9. Button lồng trong một button khác**

Chúng ta có thể nhóm các button lại với nhau trên cùng kích thướt

{:refdef: style="text-align: center;"}
![button6](/images/post/boostrap/button6.png){:class="img-responsive"}
{: refdef}

<br>
{% highlight html  linenos %}

 <div class="btn-group">
  <button type="button" class="btn btn-primary">Apple</button>
  <button type="button" class="btn btn-primary">Samsung</button>
  <div class="btn-group">
    <button type="button" class="btn btn-primary dropdown-toggle" data-toggle="dropdown">
       Sony
    </button>
    <div class="dropdown-menu">
      <a class="dropdown-item" href="#">Tablet</a>
      <a class="dropdown-item" href="#">Smartphone</a>
    </div>
  </div>
</div>  

{% endhighlight %}

