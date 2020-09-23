---
layout: course-bootstrap
title: Sử dụng list trong boostrap 
slug : bootstrap-list
category: laptrinhweb
tags: [bootstrap]
summery: List
image:
description : Giới thiệu về list, hướng dẫn cách sử dụng list trong lập trình web.
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>list</b> là gì? Các sử dụng nó trong lập trình website. 

# **1. List  trong Bootstrap 4**

Để tạo được list trong web thì chúng ta sử dụng thẻ ul và class .list-group như sau

{:refdef: style="text-align: center;"}
![list1](/images/post/boostrap/list1.png){:class="img-responsive"}
{: refdef}

<br>
{% highlight html  linenos %}

 <ul class="list-group">
  <li class="list-group-item">First item</li>
  <li class="list-group-item">Second item</li>
  <li class="list-group-item">Third item</li>
</ul> 


{% endhighlight %}

# **2. Hightlight List  trong Bootstrap 4**

Để làm hightlight một phần tử trong list ta sử dụng class .active như sau.

{:refdef: style="text-align: center;"}
![list2](/images/post/boostrap/list2.png){:class="img-responsive"}
{: refdef}

<br>
{% highlight html  linenos %}

 <ul class="list-group">
  <li class="list-group-item active">Active item</li>
  <li class="list-group-item">Second item</li>
  <li class="list-group-item">Third item</li>
</ul> 
{% endhighlight %}

# **3. Liên kết trong list**

Chúng ta có thể tạo ra một list (danh sách) và mỗi phần tử trong danh sách sẽ link tới một địa chỉ URL. Chúng ta sử dụng thẻ div thay cho thẻ ul

<br>
{% highlight html  linenos %}

 <div class="list-group">
  <a href="#" class="list-group-item list-group-item-action">First item</a>
  <a href="#" class="list-group-item list-group-item-action">Second item</a>
  <a href="#" class="list-group-item list-group-item-action">Third item</a>
</div> 

{% endhighlight %}

# **4. Disable các phần tử trong list**

Chúng ta có thể làm mờ đi các phần tử trong list không cho người dùng bấm vào bằng cách sử thuộc tính disabled

{:refdef: style="text-align: center;"}
![list3](/images/post/boostrap/list3.png){:class="img-responsive"}
{: refdef}

<br>
{% highlight html  linenos %}

 <div class="list-group">
  <a href="#" class="list-group-item disabled">Disabled item</a>
  <a href="#" class="list-group-item disabled">Disabled item</a>
  <a href="#" class="list-group-item">Third item</a>
</div> 

{% endhighlight %}


# **5. Xoá border xung quanh các phần tử trong list**

Để tạo 1 list không có border chúng ta sử dụng class .list-group-flush. Chúng sẽ xoá đi border và góc tròn xung quanh list

<br>
{% highlight html  linenos %}

 <ul class="list-group list-group-flush">
  <li class="list-group-item">First item</li>
  <li class="list-group-item">Second item</li>
  <li class="list-group-item">Third item</li>
  <li class="list-group-item">Fourth item</li>
</ul> 

{% endhighlight %}

# **6. Hiển thị danh sách list theo chiều ngang**

Nếu chúng ta muốn danh sách hiển thị theo chiều ngang màn hình thì chúng ta sử dụng class .list-group-horizontal trong .list-group như sau

<br>
{% highlight html  linenos %}

 <ul class="list-group list-group-horizontal">
  <li class="list-group-item">First item</li>
  <li class="list-group-item">Second item</li>
  <li class="list-group-item">Third item</li>
  <li class="list-group-item">Fourth item</li>
</ul> 

{% endhighlight %}

# **7.Thêm màu sắc cho các phần tử**

Chúng ta có thể sử dụng các class sau đây để tạo màu sách cho các phần tử trong list như : .list-group-item-success, list-group-item-secondary, list-group-item-info, list-group-item-warning, .list-group-item-danger, .list-group-item-primary, list-group-item-dark and list-group-item-light

{:refdef: style="text-align: center;"}
![list4](/images/post/boostrap/list4.png){:class="img-responsive"}
{: refdef}

<br>
{% highlight html  linenos %}

 <ul class="list-group">
  <li class="list-group-item list-group-item-success">Success item</li>
  <li class="list-group-item list-group-item-secondary">Secondary item</li>
  <li class="list-group-item list-group-item-info">Info item</li>
  <li class="list-group-item list-group-item-warning">Warning item</li>
  <li class="list-group-item list-group-item-danger">Danger item</li>
  <li class="list-group-item list-group-item-primary">Primary item</li>
  <li class="list-group-item list-group-item-dark">Dark item</li>
  <li class="list-group-item list-group-item-light">Light item</li>
</ul>  

{% endhighlight %}

# **8. Thêm badges cho các phần tử**

{:refdef: style="text-align: center;"}
![list5](/images/post/boostrap/list5.png){:class="img-responsive"}
{: refdef}

<br>
{% highlight html  linenos %}

 <ul class="list-group">
  <li class="list-group-item list-group-item-success">Success item</li>
  <li class="list-group-item list-group-item-secondary">Secondary item</li>
  <li class="list-group-item list-group-item-info">Info item</li>
  <li class="list-group-item list-group-item-warning">Warning item</li>
  <li class="list-group-item list-group-item-danger">Danger item</li>
  <li class="list-group-item list-group-item-primary">Primary item</li>
  <li class="list-group-item list-group-item-dark">Dark item</li>
  <li class="list-group-item list-group-item-light">Light item</li>
</ul>  

{% endhighlight %}







