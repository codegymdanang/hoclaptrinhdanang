---
layout: course-javascript
title: Sử dụng Function  
slug : javascript-function
category: laptrinhjavascript
tags: [javascript]
summery: Function   
image: /images/blog/feature_javascript.png
description : Giới thiệu về function trong Javascrip, cách hoạt động của function trong Javascript
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>function</b>là như thế nào?

# **1. function là gì**

Trong Javascript một function cho phép chúng ta đặt nhiều dòng code ở trong nó. Chúng ta phải đặt tên cho một function và sử dụng nó nhiều lần nếu mình cần

Để định nghĩa một function trong javascript chúng ta dùng từ khoá function

- Cú pháp

{% highlight javascript  linenos %}

//defining a function
function <function-name>()
{
    // code to be executed
};

//calling a function
<function-name>();

{% endhighlight %}

- Ví dụ chúng ta định nghĩa 1 function về hiển thị thông báo.

{% highlight javascript  linenos %}

function ShowMessage() {
    alert("Hello World!");
}

ShowMessage(); // chúng ta gọi function
{% endhighlight %}

# **2. function với tham số**

Chúng ta có thể thêm 1 hoặc nhiều tham số vào trong function. Chỗ nào gọi function thì thêm đối số vào. Ví dụ ta có function là hiển thị tên, khi đối số truyền vào là firstName và lastName như thế nào thì mình hiển thị thông báo chào cho người dùng.

{% highlight javascript  linenos %}

function ShowMessage(firstName, lastName) {
    alert("Hello " + firstName + " " + lastName);
}

ShowMessage("Steve", "Jobs");
ShowMessage("Bill", "Gates");

{% endhighlight %}


# **3. Trả về kết quả trong function**

Sau khi function làm việc có thể trả về hoặc không trả về kết quả. Để trả về kết quả chúng ta dùng từ khoá return như sau.

{% highlight javascript  linenos %}

function Sum(val1, val2) {
    return val1 + val2;
};

var result = Sum(10,20); // returns 30

{% endhighlight %}








