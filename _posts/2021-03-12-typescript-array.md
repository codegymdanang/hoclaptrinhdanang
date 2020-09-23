---
layout: course-typescript
title: Sử dụng Array  
slug : typescript-array
category: laptrinhjavascript
tags: [typescript]
summery: Array   
image: /images/blog/feature_javascript.png
description : Giới thiệu về Array trong Typescrip, cách hoạt động của Array trong Typescrip
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>Array</b> là như thế nào? 

# **1. Array là gì**

Chúng ta sử dụng Array để chứa nhiều giá trị . Typescript Array cũng giống như của JavaScript chúng ta có thể tạo nó bằng [ ] hoặc đối tượng Array

{% highlight javascript  linenos %}

let fruits: Array<string>;
fruits = ['Apple', 'Orange', 'Banana']; 

let ids: Array<number>;
ids = [23, 34, 100, 124, 44]; 

{% endhighlight %}

Array có thể chức đụng các phần tử khác kiểu dữ liệu

{% highlight javascript  linenos %}

let values: (string | number)[] = ['Apple', 2, 'Orange', 3, 4, 'Banana']; 
// or 
let values: Array<string | number> = ['Apple', 2, 'Orange', 3, 4, 'Banana']; 
{% endhighlight %}

# **2. Truy cập các phần tử trong Array**

Chúng ta sử dụng Index (vị trí) để truy cập các phần tử trong Array

{% highlight javascript  linenos %}

let fruits: string[] = ['Apple', 'Orange', 'Banana']; 
fruits[0]; // returns Apple
fruits[1]; // returns Orange
fruits[2]; // returns Banana
fruits[3]; // returns undefined

{% endhighlight %}

# **3. Duyệt các phần tử trong Array**

Chúng ta có thể dùng vòng lặp để duyệt qua mảng

{% highlight javascript  linenos %}

let fruits: string[] = ['Apple', 'Orange', 'Banana']; 

for(var index in fruits)
{ 
    console.log(fruits[index]);  // output: Apple Orange Banana
}

for(var i = 0; i < fruits.length; i++)
{ 
    console.log(fruits[i]); // output: Apple Orange Banana
}

{% endhighlight %}

# **4. Các phương thức hỗ trợ trong Array**

Array có sẳn các phương thức giúp chúng ta lấy các phần tử, thêm các phần tử, filter, sort các phần tử vv trong mảng

{% highlight javascript  linenos %}

var fruits: Array<string> = ['Apple', 'Orange', 'Banana']; 
fruits.sort(); 
console.log(fruits); //output: [ 'Apple', 'Banana', 'Orange' ]

console.log(fruits.pop()); //output: Orange

fruits.push('Papaya'); 
console.log(fruits); //output: ['Apple', 'Banana', 'Papaya']

fruits = fruits.concat(['Fig', 'Mango']); 
console.log(fruits); //output: ['Apple', 'Banana', 'Papaya', 'Fig', 'Mango'] 

console.log(fruits.indexOf('Papaya'));//output: 2

{% endhighlight %}



















