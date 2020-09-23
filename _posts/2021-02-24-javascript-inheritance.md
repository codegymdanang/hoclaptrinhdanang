---
layout: course-javascript
title: Kế thừa  
slug : javascript-inheritance
category: laptrinhjavascript
tags: [javascript]
summery: Kế thừa   
image: /images/blog/feature_javascript.png
description : Giới thiệu về Kế thừa trong Javascrip, cách hoạt động của Kế thừa trong Javascript
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>Kế thừa</b> là như thế nào? 

# **1. Kế thừa là gì**

Kế thừa là một khái niệm quan trọng trong lập trình hướng đối tượng. Một đối tượng kế thừa một đối tượng khác thì nó sẽ có thuộc tính và phương thức có sẳn của đối tượng mà nó kế thừa

Trong Javascript, kế thừa được hỗ trợ khi ta dùng Prototype.

Hãy xem ví dụ sau về đối tượng Student kế thừa từ đối tượng Person

{% highlight javascript  linenos %}

function Person(firstName, lastName) {
    this.FirstName = firstName || "unknown";
    this.LastName = lastName || "unknown";
};

Person.prototype.getFullName = function () {
    return this.FirstName + " " + this.LastName;
}

{% endhighlight %}

Ở ví dụ trên ta định nghĩa lớp Person có 2 thuộc tính là firstNam và lastName. Đồng thời chúng ta sử dụng prototype tạo thêm phương thức getFullName cho đối tượng Person

Bây giờ chúng ta sẽ tạo đối tượng Student kế thừa đối tượng Person và mặc định nó sẽ kế thừa 2 thuộc tính là firstName, lastName và phương thức getFullName của Person

{% highlight javascript  linenos %}

function Student(firstName, lastName, schoolName, grade)
{
    Person.call(this, firstName, lastName);

    this.SchoolName = schoolName || "unknown";
    this.Grade = grade || 0;
}

Student.prototype = new Person();
Student.prototype.constructor = Student

{% endhighlight %}

Chúng ta sử dụng Student.prototype để tạo ra đối tượng Persion

# **2. Ví dụ hoàn chỉnh về kế thừa**

{% highlight javascript  linenos %}


function Person(firstName, lastName) {
    this.FirstName = firstName || "unknown";
    this.LastName = lastName || "unknown";            
}

Person.prototype.getFullName = function () {
    return this.FirstName + " " + this.LastName;
}
function Student(firstName, lastName, schoolName, grade)
{
    Person.call(this, firstName, lastName);

    this.SchoolName = schoolName || "unknown";
    this.Grade = grade || 0;
}
//Student.prototype = Person.prototype;
Student.prototype = new Person();
Student.prototype.constructor = Student;

var std = new Student("James","Bond", "XYZ", 10);
            
alert(std.getFullName()); // James Bond
alert(std instanceof Student); // true
alert(std instanceof Person); // true


{% endhighlight %}




