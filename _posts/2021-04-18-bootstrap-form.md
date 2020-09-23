---
layout: course-bootstrap
title: Sử dụng form trong boostrap 
slug : bootstrap-form
category: laptrinhweb
tags: [bootstrap]
summery: Form
image:
description : Giới thiệu về form, hướng dẫn cách sử dụng form trong lập trình web.
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>form</b> là gì? Các sử dụng nó trong lập trình website. 

# **1. Form trong Bootstrap 4**

Trong Boostrap hỗ trợ chúng ta 2 loại form là Staked Form (form tràn màn hình) và inline Form (form trên cùng 1 dòng).



# **2. Staked Form trong Bootstrap 4**

Chúng ta sử dụng class form-group và form-control

<br>
{% highlight html  linenos %}

 <form action="/action_page.php">
  <div class="form-group">
    <label for="email">Email address:</label>
    <input type="email" class="form-control" placeholder="Enter email" id="email">
  </div>
  <div class="form-group">
    <label for="pwd">Password:</label>
    <input type="password" class="form-control" placeholder="Enter password" id="pwd">
  </div>
  <div class="form-group form-check">
    <label class="form-check-label">
      <input class="form-check-input" type="checkbox"> Remember me
    </label>
  </div>
  <button type="submit" class="btn btn-primary">Submit</button>
</form> 

{% endhighlight %}

{:refdef: style="text-align: center;"}
![stackedform](/images/post/boostrap/stackedform.png){:class="img-responsive"}
{: refdef}


# **2. Inline Form trong Bootstrap 4**

Chúng ta sử dụng class form-inline để tạo các thành phần trên một dòng.
<br>
{% highlight html  linenos %}

 <form class="form-inline" action="/action_page.php">
  <label for="email">Email address:</label>
  <input type="email" class="form-control" placeholder="Enter email" id="email">
  <label for="pwd">Password:</label>
  <input type="password" class="form-control" placeholder="Enter password" id="pwd">
  <div class="form-check">
    <label class="form-check-label">
      <input class="form-check-input" type="checkbox"> Remember me
    </label>
  </div>
  <button type="submit" class="btn btn-primary">Submit</button>
</form> 

{% endhighlight %}

{:refdef: style="text-align: center;"}
![inline form](/images/post/boostrap/inline.png){:class="img-responsive"}
{: refdef}


# **3. Form Validation trong Bootstrap 4**

Chúng ta có thể thêm điều kiện để kiểm tra nếu người dùng không nhập vào ô username hoặc password thì mình sẽ thông báo lỗi. Để form có thể thông báo được lỗi thì chúng ta kết hợp thêm javascript (trong trường hợp này là Jquery) để hiển thị thông báo.

<br>
{% highlight html  linenos %}

 <form action="/action_page.php" class="needs-validation" novalidate>
  <div class="form-group">
    <label for="uname">Username:</label>
    <input type="text" class="form-control" id="uname" placeholder="Enter username" name="uname" required>
    <div class="valid-feedback">Valid.</div>
    <div class="invalid-feedback">Please fill out this field.</div>
  </div>
  <div class="form-group">
    <label for="pwd">Password:</label>
    <input type="password" class="form-control" id="pwd" placeholder="Enter password" name="pswd" required>
    <div class="valid-feedback">Valid.</div>
    <div class="invalid-feedback">Please fill out this field.</div>
  </div>
  <div class="form-group form-check">
    <label class="form-check-label">
      <input class="form-check-input" type="checkbox" name="remember" required> I agree on blabla.
      <div class="valid-feedback">Valid.</div>
      <div class="invalid-feedback">Check this checkbox to continue.</div>
    </label>
  </div>
  <button type="submit" class="btn btn-primary">Submit</button>
</form>

<script>
// Disable form submissions if there are invalid fields
(function() {
  'use strict';
  window.addEventListener('load', function() {
    // Get the forms we want to add validation styles to
    var forms = document.getElementsByClassName('needs-validation');
    // Loop over them and prevent submission
    var validation = Array.prototype.filter.call(forms, function(form) {
      form.addEventListener('submit', function(event) {
        if (form.checkValidity() === false) {
          event.preventDefault();
          event.stopPropagation();
        }
        form.classList.add('was-validated');
      }, false);
    });
  }, false);
})();
</script> 


{% endhighlight %}



{:refdef: style="text-align: center;"}
![validation form](/images/post/boostrap/validationform.png){:class="img-responsive"}
{: refdef}
