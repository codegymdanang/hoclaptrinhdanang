---
layout: course-javascript
title: Sử dụng Array  
slug : javascript-array
category: laptrinhjavascript
tags: [javascript]
summery: Mảng   
image: /images/blog/feature_javascript.png
description : Giới thiệu về Array trong Javascrip, cách hoạt động của Array trong Javascript
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>Array</b>là như thế nào?

# **1. Mảng là gì**

Chúng ta thấy trong các bài viết trước một biến chỉ lưu trữ được 1 giá trị ví dụ như var i = 1. Nếu chúng ta muốn 1 biến chưa nhiều hơn 1 giá trị ví dụ như 10 giá trị thì ta sẽ sử dụng Array.

Array là một loại biến đặt biệt nó có thể chứa đựng nhiều giá trị trong đó. Mỗi giá trị sẽ tương ứng với một vị trị trong Array, mình gọi đó là Index. Trong Array Index được đếm bắt đầu từ 0.

# **2. Khai báo Mảng**

- Cách 1 : Chúng ta khai báo Array như sau

Cú pháp

{% highlight javascript  linenos %}

var <array-name> = [element0, element1, element2,... elementN];

{% endhighlight %}

Ví dụ ta định nghĩa và khởi tạo mảng như sau

{% highlight javascript  linenos %}

var stringArray = ["one", "two", "three"];

var numericArray = [1, 2, 3, 4];

var decimalArray = [1.1, 1.2, 1.3];

var booleanArray = [true, false, false, true];

var mixedArray = [1, "two", "three", 4];

{% endhighlight %}

- Cách 2 : chúng ta sử dụng new đối tượng Array

Cú pháp

{% highlight javascript  linenos %}

var arrayName = new Array();

var arrayName = new Array(Number length);

var arrayName = new Array(element1, element2, element3,... elementN);

{% endhighlight %}

Ví dụ 

{% highlight javascript  linenos %}

var stringArray = new Array();
stringArray[0] = "one";
stringArray[1] = "two";
stringArray[2] = "three";
stringArray[3] = "four";

var numericArray = new Array(3);
numericArray[0] = 1;
numericArray[1] = 2;
numericArray[2] = 3;

var mixedArray = new Array(1, "two", 3, "four");

{% endhighlight %}

# **3. Lấy các phần tử trong Mảng**

Chúng ta sử dụng Index (vị trí) của các đối tượng trong mảng để lấy ra giá trị của nó. Hãy luôn nhớ rằng Mảng luôn bắt đầu từ vị trị 0 chứ không phải là 1.

{% highlight javascript  linenos %}

var stringArray = new Array("one", "two", "three", "four");

stringArray[0]; // returns "one"
stringArray[1]; // returns "two"
stringArray[2]; // returns "three"
stringArray[3]; // returns "four"

var numericArray = [1, 2, 3, 4];
numericArray[0]; // returns 1
numericArray[1]; // returns 2
numericArray[2]; // returns 3
numericArray[3]; // returns 4

{% endhighlight %}

# **4. Độ dài của mảng Mảng**

Để biết được kích thướt và độ dài của mảng có bao nhiêu phần tử ta sử dụng từ khoá length


{% highlight javascript  linenos %}

var stringArray = new Array("one", "two", "three", "four");

var len = stringArray.length // kết quả là 4

{% endhighlight %}

# **5. Các phương thức có sẳn trong Mảng**

Array có hỗ trợ sẳn các phương thức để thao tác với các phần tử trong mảng như concat() , filter(), forEach(), join(), map(), pop(), push(), reduce(), reverse(), slice(), sort(), toString(), unship() để thao tác với các phần tử trong mảng. Các phương thức hay dùng nhất là 
+ pop xoá 1 phần tử khỏi mảng
+ push là thêm 1 phần tử vào màng 
+ slice cắt mảng      




