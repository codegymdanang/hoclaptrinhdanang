---
layout: course-angular
title: Angular Databinding  
slug : angular-databinding
category: laptrinhweb
tags: [angular]
summery: Data Binding   
image: /images/blog/angular.png
description : Sử dụng data binding trong dự án angular. Hướng dẫn cài đặt data binding vào dự án Angular. Hướng dẫn các tạo một ứng dụng data binding vào dự án.
youtubeId: 0734nF0B_BM
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người cách <b>sử dụng data binding</b> là như thế nào?

# **Data binding là gì**

Databinding là kỷ thuật nơi dữ liệu được đồng bộ giữa component và tầng view (template file html). Ví dụ khi người dùng cập nhật data ở tầng view thì Angular cũng cập nhật giá trị đó ở component.

Data binding trong Angular có thể chia ra làm 2 nhóm. Đó là one way binding (binding 1 chiều) và two way binding (binding 2 chiều).

# **One way binding là gì**

- One way binding thì dữ liệu được truyền 1 chiều. Có thể từ view sang component hoặc ngược lại từ component sang view.

- Từ component sang view chúng ta sử sụng Interpolation & Property Binding để hiển thị dữ liệu như sau
+ Chúng ta sử dụng {{ }} để hiển thị giá trị từ component sang view

Ví dụ ta có component là 

{% highlight javascript  linenos %}

import { Component } from '@angular/core';
 
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  firstName= 'Sachin';
  lastName=”Tendulkar”
}

{% endhighlight %}

Như vậy dữ liệu trong component này có là firstName và lastName. Ta hiển thị bên View như sau



Welcome, {{firstName}} {{lastName}}


- Ngược lại nếu từ View truyền dữ liệu về component thì ta dùng Property binding như sau [binding-target]=”binding-source”

{% highlight html  linenos %}

<h1 [innerText]="title"></h1>
<h2>Example 1</h2>
<button [disabled]="isDisabled">I am disabled</button>

{% endhighlight %}

{% highlight javascript  linenos %}

import { Component } from '@angular/core';
 
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title="Angular Property Binding Example"
  
  //Example 1
  isDisabled= true;
 
}
{% endhighlight %}

- Event Binding chúng ta sử dụng để bind các sự kiện như click chuột, sự kiện bàn phím etc. Chúng ta sử dụng cú pháp sau để thực hiện sự kiện khi chuột click vô nút Save. Sau đó nó sẽ gọi hàm onSave bên class component

{% highlight html  linenos %}

<button (click)="onSave()">Save</button>

{% endhighlight %}

{% highlight javascript  linenos %}

import { Component } from '@angular/core';
 
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  firstName= 'Sachin';
  lastName=”Tendulkar”

  onSave() {
    //xử lý nút Save
  }

}

{% endhighlight %}

# **Two way binding là gì**

Binding 2 chiều có nghĩa là chúng ta thay đỗi dữ liệu từ component qua view và ngược lại từ view chúng ta thay đỗi dữ liệu. 

2 way biding thì hữu dụng khi mình làm form. Chúng ta sử dụng ngModel để thực hiện việc binding 2 chiều.

{% highlight html  linenos %}

<h2>Example 2</h2>
<input type="text" name="value" [(ngModel)]="value">
<p> You entered {{value}}</p>
<button (click)="clearValue()">Clear</button>

{% endhighlight %}


{% highlight javascript  linenos %}

import { Component } from '@angular/core';
 
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {

  value="";

  clearValue() {
   this.value="";
 }

}

{% endhighlight %}









