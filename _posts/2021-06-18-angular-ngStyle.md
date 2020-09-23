---
layout: course-angular
title: Sử dụng Directive ngStyle
slug : angular-ngStyle
category: laptrinhweb
tags: [angular]
summery: NgStyle 
image: /images/blog/angular.png
description : Thêm ngStyle trong dự án angular. Hướng dẫn sử dụng ngStyle vào dự án Angular. Hướng dẫn các tạo ngStyle vào dự án.
youtubeId: 0734nF0B_BM
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người cách tạo <b>ngStyle</b> là như thế nào? 

# **1. ngStyle là gì**

Chúng ta sử dụng ngStyle có thể tạo nhiều thuộc tính css trong phần tử html. Các đều kiện sẽ được đánh giá lúc chương trình đang chạy và gán giá trị vào trong thẻ html.

- Cú pháp ngIf như sau

{% highlight html  linenos %}

<element [ngStyle]="{'styleNames': styleExp}">...</element>

{% endhighlight %}

- ngStyle là nơi chúng ta sử dụng các css như font-size, color, width, height như ví dụ dưới đây.

{% highlight html  linenos %}
<some-element [ngStyle]="{'font-size': '20px'}">Set Font size to 20px</some-element>
{% endhighlight %}

# **2. ngStyle thay đổi style động**

- Trong file component class ta có biến color như sau

{% highlight html  linenos %}

color: string= 'red';

{% endhighlight %}

- Chúng ta sử dụng nó qua bên template html như sau

{% highlight html  linenos %}

<input [(ngModel)]="color" /> 
<div [ngStyle]="{'color': color}">Change my color</div>
{% endhighlight %}

# **3. ngStyle nhiều thuộc tính**

{% highlight html  linenos %}

<p [ngStyle]="{'color': 'purple',
               'font-size': '20px',
               'font-weight': 'bold'}">
     Multiple styles
</p>
{% endhighlight %}

# **4. ngStyle sử dụng đối tượng**

- Chúng ta tạo file StyleClass

{% highlight html  linenos %}

class StyleClass {
   'color': string= 'blue';
   'font-size.px': number= 20;
   'font-weight': string= 'bold'; 
}
{% endhighlight %}

- Chúng ta tạo đối tượng StyleClass trong component class

{% highlight javascript  linenos %}

styleClass: StyleClass = new StyleClass();

{% endhighlight %}

- Chúng ta sử dụng trong template html

{% highlight html  linenos %}

<div [ngStyle]="styleClass">size & Color</div>

{% endhighlight %}



