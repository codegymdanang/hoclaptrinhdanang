---
layout: course-typescript
title: Sử dụng vòng lặp  
slug : typescript-loop
category: laptrinhjavascript
tags: [typescript]
summery: Vòng lặp   
image: /images/blog/feature_javascript.png
description : Giới thiệu về vòng lặp trong Typescrip, cách hoạt động của vòng lặp trong Typescrip
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>vòng lặp</b> là như thế nào? 

# **1. Vòng lặp for**

Typescript hỗ trợ cho chúng ta 3 loại vòng lặp for là forloop , for of loop và for in loop

- Vòng lặp for Loop

Cú pháp

{% highlight javascript  linenos %}

for (first expression; second expression; third expression ) {
    // statements to be executed repeatedly
}

{% endhighlight %}


Ví dụ

{% highlight javascript  linenos %}

for (let i = 0; i < 3; i++) {
  console.log ("Block statement execution no." + i);
}

{% endhighlight %}

- Vòng lăp for of Loop

Dùng để trả lại từng phần tử của tập hợp. Nó tiện hơn vòng lặp for . Vì vòng lặp for trả về index, dựa vào index ta mới lấy được phần tử. 

Ví dụ

{% highlight javascript  linenos %}

let arr = [10, 20, 30, 40];

for (var val of arr) {
  console.log(val); // prints values: 10, 20, 30, 40
}

{% endhighlight %}

- Vòng lăp for in Loop

Duyệt qua các phần tử của mảng và trả về vị trí index của các phần tử trong mảng

{% highlight javascript  linenos %}

let arr = [10, 20, 30, 40];

for (var index in arr) {
  console.log(index); // prints indexes: 0, 1, 2, 3

  console.log(arr[index]); // prints elements: 10, 20, 30, 40
}

{% endhighlight %}

# **2. Vòng lặp While**

Nó cũng tương tự nguyên lý vòng lặp while bên javascript. Kiểm tra điều kiện trước khi chạy các dòng code trong while

Cú pháp

{% highlight javascript  linenos %}

while (condition expression) {
    // code block to be executed
}

{% endhighlight %}

Ví dụ

{% highlight javascript  linenos %}

let i: number = 2;

while (i < 4) {
    console.log( "Block statement execution no." + i )
    i++;
}

{% endhighlight %}


# **3. Vòng lặp doWhile**

Vòng lặp dowhile thì mình chạy các câu lệnh trong do trước sau đó kiểm tra điều kiện. Vòng lặp dowhile ít nhất chạy 1 lần cho dù điều kiện không thoả mản. 

Cú pháp

{% highlight javascript  linenos %}

do {
// code block to be executed
}
while (condition expression);

{% endhighlight %}

Ví dụ

{% highlight javascript  linenos %}

let i: number = 2;
do {
    console.log("Block statement execution no." + i )
    i++;
} while ( i < 4)

{% endhighlight %}






















