---
layout: course-javascript
title: Khai báo biến   
slug : javascript-variable
category: laptrinhjavascript
tags: [javascript]
summery: Biến   
image: /images/blog/feature_javascript.png
description : Giới thiệu về Biến trong Javascrip, cách hoạt động của Biến trong Javascript
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>Biến</b>là như thế nào?

# **1. Biến là gì**

Chúng ta sử dụng biến để lưu lại các giá trị. Giá trị này có thể thay đổi bất cứ lúc nào. Trong Javascript chúng ta sử dung từ khoá var để khai báo một biến. Tên biến phải là duy nhất và không được đặt trùng tên với các biến khác. Chúng ta sử dụng dấu = để gán giá trị cho biến

# **2. Khai báo Biến**

- Cú pháp khai báo biến

{% highlight javascript  linenos %}

var <variable-name>;

var <variable-name> = <value>;


{% endhighlight %}

- Ví dụ khai báo biến và giá trị mà nó sẽ chứa

{% highlight javascript  linenos %}

var one = 1; // variable stores numeric value

var two = 'two';  // variable stores string value

var three;

{% endhighlight %}

- Chúng ta có thể khai báo nhiều biến trên cùng 1 dòng

{% highlight javascript  linenos %}

var one = 1, two = 'two', three;

{% endhighlight %}

- Chúng ta có thể khai báo biến không cần dùng từ khoá var vẫn được. Nhưng anh khuyên nên dùng để code dể đọc và dể hiểu

{% highlight javascript  linenos %}

one = 1;

two = 'two';

{% endhighlight %}

# **3. Đặt tên cho biến**

Tên của biến là một phần rất quan trọng trong sử dụng biến. Đặt tên biến phải bắt đầu bằng ký tự (a-z hoặc A-Z), hoặc dấu _ hoặc dấu $. Tiếp sau đó có thể là số (0-9). Tên biến trong JS phân biệt chữ hoa và chữ thường chính vì vậy mà tên biến là x thì sẽ khác với X

- Ví dụ khai báo đúng tên biến

{% highlight javascript  linenos %}

var x = 10;  
var $value="sonoo";  

{% endhighlight %}


















