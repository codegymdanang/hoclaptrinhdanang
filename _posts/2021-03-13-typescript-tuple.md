---
layout: course-typescript
title: Sử dụng Tuple  
slug : typescript-tuple
category: laptrinhjavascript
tags: [typescript]
summery: Tuple   
image: /images/blog/feature_javascript.png
description : Giới thiệu về Tuple trong Typescrip, cách hoạt động của Tuple trong Typescrip
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>Tuple</b> là như thế nào? 

# **1. Tuple là gì**

Chúng ta sử dụng Tuple để chứa 2 hoăc nhiều gía trị có kiểu dữ liệu khác nhau, ví dụ như có thể chứa string và number trong ví dụ sau.

{% highlight javascript  linenos %}

var empId: number = 1;
var empName: string = "Steve";        

// Tuple type variable 
var employee: [number, string] = [1, "Steve"];

{% endhighlight %}

# **2. Tuple chứa nhiều giá trị**

Tuple có the chứa nhiều giá trị có kiểu dữ liệu khác nhau như sau

{% highlight javascript  linenos %}

var employee: [number, string] = [1, "Steve"];
var person: [number, string, boolean] = [1, "Steve", true];

var user: [number, string, boolean, number, string];// declare tuple variable
user = [1, "Steve", true, 20, "Admin"];// initialize tuple variable

{% endhighlight %}


# **3. Tuple Array**

Chúng ta có thể sử dụng một mảng Tuple 

{% highlight javascript  linenos %}

var employee: [number, string][];
employee = [[1, "Steve"], [2, "Bill"], [3, "Jeff"]];

{% endhighlight %}

Chúng ta truy cập mảng tuple như sau

{% highlight javascript  linenos %}

var employee: [number, string] = [1, "Steve"];
employee[0]; // returns 1
employee[1]; // returns "Steve"

{% endhighlight %}

# **4. Thêm phần tử vào Tuple**

Chúng ta sử dụng push để thêm phần tử cho tuple

{% highlight javascript  linenos %}

var employee: [number, string] = [1, "Steve"];
employee.push(2, "Bill"); 
console.log(employee); //Output: [1, 'Steve', 2, 'Bill']

{% endhighlight %}

# **5. Các phương thức hỗ trợ trong Tuple**

Tuple cũng giống như Array, chúng ta có thể sử dụng các method có sẳn trong Array cho tuple như pop, push, concat etc

{% highlight javascript  linenos %}

var employee: [number, string] = [1, "Steve"];

// retrieving value by index and performing an operation 
employee[1] = employee[1].concat(" Jobs"); 
console.log(employee); //Output: [1, 'Steve Jobs']

{% endhighlight %}







