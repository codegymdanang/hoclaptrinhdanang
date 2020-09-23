---
layout: course-javascript
title: Vòng lặp  
slug : javascript-loop
category: laptrinhjavascript
tags: [javascript]
summery: Vòng lặp   
image: /images/blog/feature_javascript.png
description : Giới thiệu về vòng lặp trong Javascrip, cách hoạt động của vòng lặp trong Javascript
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>vòng lặp</b>là như thế nào?

# **1. Vòng lặp for là gì**

Chúng ta sử dụng vòng lặp để thực hiện đi thực hiện lại những dòng code trong vòng lặp tới khi điều kiện không còn thoả mãn nữa.

- Cú pháp

{% highlight javascript  linenos %}

for(initializer; condition; iteration)
{
    // Code to be executed
}

{% endhighlight %}

Vòng lặp for cần 3 thành phần đó là

initializer : khởi tạo giá trị ban đầu
condition   : điều kiện kết thúc vòng lặp
iteration   : biến đếm vòng lặp có thể tăng lên hoặc giảm xuống

- Ví dụ

{% highlight javascript  linenos %}

for (var i = 0; i < 5; i++)
{
    console.log(i);
}
{% endhighlight %}

Trong vòng lặp loop 3 thành phần có thể không cần thiết khai báo , mình chỉ cần khai báo giá trị initializer trước khi vòng lặp chạy vẫn được. Nhưng cách này anh khuyên không nên dùng vì gây khó hiểu

{% highlight javascript  linenos %}

var arr = [10, 11, 12, 13, 14];
var i = 0;

for (; ;) {
    
    if (i >= 5)
    break;

    console.log(arr[i]);
        
    i++;
}
{% endhighlight %}

# **2. Vòng lặp while là gì**

Vòng lặp While sẽ thực hiện các dòng code ở trong nó cho đến khi điều kiện không thoả mãn. Khác với vòng lặp for ta biết trước số lần vòng lặp sẽ chạy còn vòng lặp while thì không biết trước

- Cú pháp

{% highlight javascript  linenos %}

while(condition expression)
{
    //code ở đây
}
{% endhighlight %}

- Ví dụ 

{% highlight javascript  linenos %}

var i =0;

while(i < 5)
{
    console.log(i);
    i++;
}
{% endhighlight %}

# **3. Vòng lặp do-while là gì**

Cũng giống như vòng lặp while. Vòng lặp do-while chạy cho đến khi điều kiện không còn đúng nữa. Khác ở vòng lặp while ở chỗ do-while luôn luôn chạy 1 lần dù có điều kiện có sai.

- Cú pháp

{% highlight javascript  linenos %}

do{
    //code to be executed
}while(condition expression)

{% endhighlight %}

- Ví dụ

{% highlight javascript  linenos %}

var i = 0;

do{
   
     alert(i);
    i++;

} while(i < 5)
{% endhighlight %}





