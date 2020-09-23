---
layout: course-bootstrap
title: Sử dụng input trong boostrap 
slug : bootstrap-input
category: laptrinhweb
tags: [bootstrap]
summery: Input
image:
description : Giới thiệu về input, hướng dẫn cách sử dụng input trong lập trình web.
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>form</b> là gì? Các sử dụng nó trong lập trình website. Trong bootstrap hỗ trợ các loại input như input, textarea, checkbox, radio, select.

# **1. Input trong Bootstrap 4**

Boostrap hỗ trợ các loại Input HTML5 như text, password, datetime, date, month, time, week, number, email, url, tel, và color.

Ví dụ như ta muốn input có type là text (nhập đoạn text vào input) hoặc nhập vào input là dạng password thì ta chỉ định vào trong thuộc tính type của thẻ input như sau



<br>
{% highlight html  linenos %}

  <div class="form-group">
  <label for="usr">Name:</label>
  <input type="text" class="form-control" id="usr">
</div>
<div class="form-group">
  <label for="pwd">Password:</label>
  <input type="password" class="form-control" id="pwd">
</div> 

{% endhighlight %}

Chúng ta sử dụng .form-control để input có chiều rộng full màn hình.

# **2. Textarea trong Bootstrap 4**

Để tạo Textarea chúng ta sử dụng thẻ textarea như sau


<br>
{% highlight html  linenos %}

<div class="form-group">
  <label for="comment">Comment:</label>
  <textarea class="form-control" rows="5" id="comment"></textarea>
</div> 

{% endhighlight %}

# **3. Checkbox trong Bootstrap 4**

Chúng ta sử dụng type là checkbox để tạo các checkbox 

<br>
{% highlight html  linenos %}

 <div class="form-check">
  <label class="form-check-label">
    <input type="checkbox" class="form-check-input" value="">Option 1
  </label>
</div>
<div class="form-check">
  <label class="form-check-label">
    <input type="checkbox" class="form-check-input" value="">Option 2
  </label>
</div>
<div class="form-check">
  <label class="form-check-label">
    <input type="checkbox" class="form-check-input" value="" disabled>Option 3
  </label>
</div> 

{% endhighlight %}

- Nếu chúng ta mong muốn các check box nằm trên cùng 1 hàng. thì chúng ta dùng class .form-check-inline

<br>
{% highlight html  linenos %}

 <div class="form-check-inline">
  <label class="form-check-label">
    <input type="checkbox" class="form-check-input" value="">Option 1
  </label>
</div>
<div class="form-check-inline">
  <label class="form-check-label">
    <input type="checkbox" class="form-check-input" value="">Option 2
  </label>
</div>
<div class="form-check-inline">
  <label class="form-check-label">
    <input type="checkbox" class="form-check-input" value="" disabled>Option 3
  </label>
</div> 

{% endhighlight %}

# **4. Radio trong Bootstrap 4**

- Chúng ta sử dụng type là radio để tạo các radio button như sau

<br>
{% highlight html  linenos %}

 <div class="form-check">
  <label class="form-check-label">
    <input type="radio" class="form-check-input" name="optradio">Option 1
  </label>
</div>
<div class="form-check">
  <label class="form-check-label">
    <input type="radio" class="form-check-input" name="optradio">Option 2
  </label>
</div>
<div class="form-check disabled">
  <label class="form-check-label">
    <input type="radio" class="form-check-input" name="optradio" disabled>Option 3
  </label>
</div> 
{% endhighlight %}

- Nếu chúng ta muốn các radio button cùng nằm trên 1 dòng thì sử dụng class .form-check-inline

<br>
{% highlight html  linenos %}

 <div class="form-check-inline">
  <label class="form-check-label">
    <input type="radio" class="form-check-input" name="optradio">Option 1
  </label>
</div>
<div class="form-check-inline">
  <label class="form-check-label">
    <input type="radio" class="form-check-input" name="optradio">Option 2
  </label>
</div>
<div class="form-check-inline disabled">
  <label class="form-check-label">
    <input type="radio" class="form-check-input" name="optradio" disabled>Option 3
  </label>
</div> 

{% endhighlight %}

# **5. Select list trong Bootstrap 4**

Để tạo ra select list chúng ta dùng thẻ select và option như sau

<br>
{% highlight html  linenos %}

 <div class="form-group">
  <label for="sel1">Select list:</label>
  <select class="form-control" id="sel1">
    <option>1</option>
    <option>2</option>
    <option>3</option>
    <option>4</option>
  </select>
</div> 

{% endhighlight %}

# **6. Tăng kích thướt cho input trong form**

Chúng ta có thể tạo ra những input to nhỏ và trung bình bằng cách sử dụng class form-control-sm hoặc .form-control-lg như hình bên dưới.

{:refdef: style="text-align: center;"}
![input](/images/post/boostrap/input1.png){:class="img-responsive"}
{: refdef}

<br>
{% highlight html  linenos %}


<input type="text" class="form-control form-control-sm">
<input type="text" class="form-control form-control">
<input type="text" class="form-control form-control-lg"> 

{% endhighlight %}

# **7. Input Group**

Chúng ta có thể thêm icon text hoặc button trong input bằng cách sử dụng class .input-group-prepend hoặc .input-group-append

{:refdef: style="text-align: center;"}
![input2](/images/post/boostrap/input2.png){:class="img-responsive"}
{: refdef}

<br>
{% highlight html  linenos %}

 <form>
  <div class="input-group mb-3">
    <div class="input-group-prepend">
      <span class="input-group-text">@</span>
    </div>
    <input type="text" class="form-control" placeholder="Username">
  </div>

  <div class="input-group mb-3">
    <input type="text" class="form-control" placeholder="Your Email">
    <div class="input-group-append">
      <span class="input-group-text">@example.com</span>
    </div>
  </div>
</form> 

{% endhighlight %}


# **8. Input Group và Checkbox**

Chúng ta có thể kết hợp Input Group và checkbox

{:refdef: style="text-align: center;"}
![input3](/images/post/boostrap/input3.png){:class="img-responsive"}
{: refdef}

<br>
{% highlight html  linenos %}

   <div class="input-group mb-3">
  <div class="input-group-prepend">
    <div class="input-group-text">
      <input type="checkbox">
    </div>
  </div>
  <input type="text" class="form-control" placeholder="Some text">
</div>

<div class="input-group mb-3">
  <div class="input-group-prepend">
    <div class="input-group-text">
      <input type="radio">
    </div>
  </div>
  <input type="text" class="form-control" placeholder="Some text">
</div> 

{% endhighlight %}

# **9. Input Group và Button**

Chúng ta có thể kết hợp Input Group và Button

{:refdef: style="text-align: center;"}
![input4](/images/post/boostrap/input4.png){:class="img-responsive"}
{: refdef}

<br>
{% highlight html  linenos %}

 <div class="input-group mb-3">
  <div class="input-group-prepend">
    <button class="btn btn-outline-primary" type="button">Basic Button</button>
  </div>
  <input type="text" class="form-control" placeholder="Some text">
</div>

<div class="input-group mb-3">
  <input type="text" class="form-control" placeholder="Search">
  <div class="input-group-append">
    <button class="btn btn-success" type="submit">Go</button>
  </div>
</div>

<div class="input-group mb-3">
  <input type="text" class="form-control" placeholder="Something clever..">
  <div class="input-group-append">
    <button class="btn btn-primary" type="button">OK</button>
    <button class="btn btn-danger" type="button">Cancel</button>
  </div>
</div> 

{% endhighlight %}



