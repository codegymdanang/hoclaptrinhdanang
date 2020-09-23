---
layout: course-javascript
title: Kiểu dữ liệu  
slug : javascript-datatype
category: laptrinhjavascript
tags: [javascript]
summery: Kiểu dữ liệu   
image: /images/blog/feature_javascript.png
description : Giới thiệu về kiểu dữ liệu trong Javascrip, cách hoạt động của kiểu dữ liệu trong Javascript
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>kiểu dữ liệu</b>là như thế nào?

# **1. kiểu dữ liệu là gì**

Trong JavaScript ta có 2 loại kiểu dữ liệu là Primitive (String, number, Boolean, Null, và Undefined) và Non Primitive (Object, Date, Array). Chúng ta sẽ lần lượt đi qua các kiểu dữ liệu này.

# **2. kiểu dữ liệu String**

Kiểu dữ liệu String thường chứa giá trị là chuỗi. Chúng ta có thể sử dụng dấu " " hoặc ' ' 

- Ví dụ

{% highlight javascript  linenos %}

var str1 = "Hello World";

var str2 = 'Hello World';


{% endhighlight %}

- String là một kiểu dữ liệu đặt biệt vì nó gồm nhiều ký tự kết hợp lại như các em thấy chữ Hello là do các ký tự H , e ,l ,l ,o kết hợp lại với nhau. Do vậy ta có thể dể dàng lấy từng ký tự trong chuỗi Hello như sau

- Ví dụ

{% highlight javascript  linenos %}

var str = 'Hello World';

str[0] // H
str[1] // e
str[2] // l
str[3] // l
str[4] // o

{% endhighlight %}

- Nối 2 chuỗi String lại với nhau

Chúng ta sử dụng dấu + để nối các chuỗi lại với nhau.

- Ví dụ

{% highlight javascript  linenos %}

var str = 'Hello ' + "World " + 'from ' + 'TutorialsTeacher ';

{% endhighlight %}

- Sử dụng dấu ký tự đặt biệt trong chuỗi, như các em thấy dấu " và dấu ' là những ký tự đặt biệt. Nhưng nếu ta muốn sử dụng các ký tự đặt biệt trong chuỗi thì ta dù ký tự \ trước các ký tự đặt biệt

- Ví dụ

{% highlight javascript  linenos %}

var str1 = "This is \"simple\" string";

var str2 = 'This is \'simple\' string';

{% endhighlight %}

# **2. kiểu dữ liệu Number**

Kiểu dữ liệu Number sẽ chứa đựng các số nguyên, số thập phân, kiểu hex hoặc octal

- Ví dụ

{% highlight javascript  linenos %}
var int = 100;
var float = 100.5;
var hex = 0xfff;
var exponential = 2.56e3;
var octal = 030

{% endhighlight %}

# **3. kiểu dữ liệu Boolean**

Kiểu Boolean chỉ chứa đúng 2 giá trị là đúng và sai (true hoặc false)

- Ví dụ

{% highlight javascript  linenos %}

var YES = true;

var NO = false;

{% endhighlight %}

hoặc ví dụ sau

{% highlight javascript  linenos %}

alert(1 > 2); // false

alert(10< 9); // false

alert(5 == 5); // true

{% endhighlight %}

# **4. kiểu dữ liệu NULL**

Chúng ta sử dụng NULL để chỉ ra rằng biến này không chứa bất kỳ giá trị gì. Nó sẽ được gán giá trị sau. NULL có nghĩa là giá trị chưa được tạo ra cho biến.

- Ví dụ

{% highlight javascript  linenos %}

var myVar = null;

alert(myVar); // null 


{% endhighlight %}

# **5. kiểu dữ liệu Undefined** 

Biến có giá trị undefined có nghĩa là không có giá trị nào được gán cho nó trước khi sử dụng.

{% highlight javascript  linenos %}

var myVar;

alert(myVar);// undefined

{% endhighlight %}

# **6. kiểu dữ liệu Object** 

Kiểu dữ liệu Object (đối tượng) cũng giống như các kiểu khác của javascript nhưng khác nhau ở chỗ Object này sẽ chứa đựng nhiều giá trị và phương thức

- Cách 1 :  Tạo Object Literal

Chúng ta sử dụng dấu { } để tạo một đối tượng ( Object ), các thuộc tính và hành động của đối tượng đặt trong dấu { }

Cú pháp như sau

{% highlight javascript  linenos %}

var <object-name> = { key1: value1, key2: value2,... keyN: valueN};

{% endhighlight %}

Ví dụ mình tạo đối tượng person như sau

{% highlight javascript  linenos %}

var emptyObject = {}; // object with no properties or methods

var person = { firstName: "John" }; // object with single property

// object with single method
var message = { 
                showMessage: function (val) { 
                            alert(val); 
                } 
            }; 

// object with properties & method
var person = { 
                firstName: "James", 
                lastName: "Bond", 
                age: 15, 
                getFullName: function () { 
                        return this.firstName + ' ' + this.lastName 
                }
            }
{% endhighlight %}

- Cách 2 : Tạo object bằng từ khoá new

{% highlight javascript  linenos %}

var <object-name> = { key1: value1, key2: value2,... keyN: valueN};

{% endhighlight %}

Ví dụ mình tạo đối tượng person như sau

{% highlight javascript  linenos %}

var person = new Object();

// Attach properties and methods to person object     
person.firstName = "James";
person["lastName"] = "Bond"; 
person.age = 25;
person.getFullName = function () {
        return this.firstName + ' ' + this.lastName;
    };

// access properties & methods 
person.firstName; // James
person.lastName; // Bond
person.getFullName(); // James Bond

{% endhighlight %}

JavaScript sẽ trả về undefined if như ta truy cập các biến và phương thức nếu nó không tồn tại.

# **6. kiểu dữ liệu Date** 

Javascript cung cấp cho chúng ta kiểu dữ liệu Date để xử lý các dữ liệu liên qua đến ngày tháng năm, giờ phút giây.

- Ví dụ như lấy ngày giờ hiện tại

{% highlight javascript  linenos %}

Date(); //current date

//or

var currentDate = new Date(); //current date

{% endhighlight %}

- Nếu chúng ta muốn làm nhiều tính toán hơn là sử dụng ngày hiện tại . Ta có thể tạo ra đối tượng ngày với các tham số ta muốn


{% highlight javascript  linenos %}

var dt = new Date();

var dt = new Date(milliseconds);

var dt = new Date('date string');

var dt = new Date(year, month[, date, hour, minute, second, millisecond]);

var date1 = new Date("February 2015-3");

var date2 = new Date("February-2015-3");

var date3 = new Date("February-2015-3");

var date4 = new Date("February,2015-3");

var date5 = new Date("February,2015,3");

var date6 = new Date("February$2015$3");

var date7 = new Date("3-2-2015"); // MM-dd-YYYY

var date8 = new Date("3/2/2015"); // MM-dd-YYYY



{% endhighlight %}


