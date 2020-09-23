---
layout: course-typescript
title: Sử dụng Number  
slug : typescript-number
category: laptrinhjavascript
tags: [typescript]
summery: Number   
image: /images/blog/feature_javascript.png
description : Giới thiệu về Number trong Typescrip, cách hoạt động của Number trong Typescrip
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>Number</b> là như thế nào? 

# **1. Number là gì**

Chúng ta sử dụng Number khi chúng ta chứa các giá trị là số học. Tất cả Number được chứa đựng theo dạng thập phân. Number có thể là Decimal (10), Hex(16), hoặc Octal (18)

{% highlight javascript  linenos %}

let first:number = 123; // number 
let second: number = 0x37CF;  // hexadecimal
let third:number=0o377 ;      // octal
let fourth: number = 0b111001;// binary  

console.log(first);  // 123 
console.log(second); // 14287
console.log(third);  // 255
console.log(fourth); // 57 

{% endhighlight %}

# **2. Method toExponential**

{% highlight javascript  linenos %}

let myNumber: number = 123456;

myNumber.toExponential(); // returns 1.23456e+5
myNumber.toExponential(1); //returns 1.2e+5
myNumber.toExponential(2); //returns 1.23e+5
myNumber.toExponential(3); //returns 1.235e+5

{% endhighlight %}

# **3. Method toFixed**

{% highlight javascript  linenos %}

let myNumber: number = 10.8788;

myNumber.toFixed(); // returns 11
myNumber.toFixed(1); //returns 10.9
myNumber.toFixed(2); //returns 10.88
myNumber.toFixed(3); //returns 10.879
myNumber.toFixed(4); //returns 10.8788

{% endhighlight %}

# **4. Method toLocaleString**

{% highlight javascript  linenos %}

let myNumber: number = 10667.987;

myNumber.toLocaleString(); // returns 10,667.987 - US English
myNumber.toLocaleString('de-DE'); // returns 10.667,987 - German
myNumber.toLocaleString('ar-EG'); // returns 10667.987 in Arebic

{% endhighlight %}

# **5. Method toPrecision**

{% highlight javascript  linenos %}

let myNumber: number = 10.5679;

myNumber.toPrecision(1); // returns 1e+1
myNumber.toPrecision(2); // returns 11
myNumber.toPrecision(3); // returns 10.6
myNumber.toPrecision(4); // returns 10.57

{% endhighlight %}

# **6. Method toString**

{% highlight javascript  linenos %}

let myNumber: number = 123;
myNumber.toString(); // returns '123'
myNumber.toString(2); // returns '1111011'
myNumber.toString(4); // returns '1323'
myNumber.toString(8); // returns '173'
myNumber.toString(16); // returns '7b'
myNumber.toString(36); // returns '3f'

{% endhighlight %}

# **7. Method ValueOf**

{% highlight javascript  linenos %}

let myNumber = new Number(123);
console.log(myNumber) //Output: a number object with value 123
console.log(myNumber.valueOf()) //Output: 123
console.log(typeof num) //Output: object

let num2 = num.valueOf() 
console.log(num2) //Output: 123
console.log(typeof num2) //Output: number

{% endhighlight %}


















