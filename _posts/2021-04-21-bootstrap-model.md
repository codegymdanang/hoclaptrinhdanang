---
layout: course-bootstrap
title: Sử dụng Modal trong boostrap 
slug : bootstrap-modal
category: laptrinhweb
tags: [bootstrap]
summery: Modal
image:
description : Giới thiệu về modal, hướng dẫn cách sử dụng modal trong lập trình web.
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>modal</b> là gì? Các sử dụng nó trong lập trình website. 

# **1. Tạo Modal trong Bootstrap 4**

Khi chúng ta muốn hiển thị một dialog hoặc một popup trên website thì sử dụng modal

{:refdef: style="text-align: center;"}
![modal1](/images/post/boostrap/modal1.png){:class="img-responsive"}
{: refdef}

<br>
{% highlight html  linenos %}

<!-- Button to Open the Modal -->
<button type="button" class="btn btn-primary" data-toggle="modal" data-target="#myModal">
  Open modal
</button>

<!-- The Modal -->
<div class="modal" id="myModal">
  <div class="modal-dialog">
    <div class="modal-content">

      <!-- Modal Header -->
      <div class="modal-header">
        <h4 class="modal-title">Modal Heading</h4>
        <button type="button" class="close" data-dismiss="modal">&times;</button>
      </div>

      <!-- Modal body -->
      <div class="modal-body">
        Modal body..
      </div>

      <!-- Modal footer -->
      <div class="modal-footer">
        <button type="button" class="btn btn-danger" data-dismiss="modal">Close</button>
      </div>

    </div>
  </div>
</div>

{% endhighlight %}

# **2. Thêm hiệu ứng Modal trong Bootstrap 4**

Chúng ta sử dụng class .fade để thêm hiệu ứng khi mở và đóng modal

<br>
{% highlight html  linenos %}

<!-- Fading modal -->
<div class="modal fade"></div>

<!-- Modal without animation -->
<div class="modal"></div>


{% endhighlight %}

# **3. Tăng kích thước Modal trong Bootstrap 4**

Chúng ta có thể thêm kích thước của modal to hay nhỏ bằng cách sử dụng class .modal-sm hoặc modal-lg hoặc .modal-xl

<br>
{% highlight html  linenos %}

<div class="modal-dialog modal-sm">


{% endhighlight %}

<br>
{% highlight html  linenos %}

<div class="modal-dialog modal-lg">


{% endhighlight %}

<br>
{% highlight html  linenos %}

<div class="modal-dialog modal-xl">


{% endhighlight %}

Mặc định modal có kích thướt trung bình.

# **4. Modal nằm giữa màn hình trong Bootstrap 4**

Để tạo modal nằm giữa màn hình chúng ta dùng class .modal-dialog-centered 

<br>
{% highlight html  linenos %}

<div class="modal-dialog modal-dialog-centered">


{% endhighlight %}

# **5. Modal có thanh cuộn nếu nội dung bên trong nhiều**

Chúng ta có thể thêm scrollbar vào bằng việc sử dụng class .modal-dialog-scrollable  .modal-dialog

<br>
{% highlight html  linenos %}

<div class="modal-dialog modal-dialog-scrollable">

{% endhighlight %}










