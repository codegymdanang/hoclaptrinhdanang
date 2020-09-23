---
layout: course-angular
title: Thêm component con vào component cha  
slug : angular-add-child-component
category: laptrinhweb
tags: [angular]
summery: Thêm Component Con   
image: /images/blog/angular.png
description : Thêm component con trong dự án angular. Hướng dẫn cách thêm component con vào dự án Angular. Hướng dẫn các tạo một ứng dụng component vào dự án.
youtubeId: 0734nF0B_BM
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người cách thêm <b>component con</b> là như thế nào? Trong bài viết hôm nay chúng ta sẽ sử dụng Angular Cli để tạo ra component.

# **1. Component là gì**

Trong angular các component được sắp xếp theo kiến trúc component-base, nghĩa là mỗi component sẽ phụ trách một nhiệm vụ cụ thể. Ví dụ ta có nhiệm vụ là login, đăng ký, mua hàng, thì ta tạo ra 3 components mỗi component sẽ có một template html, class component và css riêng. Kiến trúc các component trong Angular giống như kiến trúc 1 cái cây. Gồm có cha, sau đó xuống con, xuống cháu.

# **2. Cú pháp tạo Component**

Chúng ta sử dụng cú pháp sau của Angular Cli để tạo ra component.

{% highlight javascript  linenos %}

ng new childComponent

{% endhighlight %}

# **3. Thêm Component con**

Để thêm 1 component con vào một component cha chúng ta thực hiện các bước sau. Trong ví dụ này ta sẽ tạo ra một component là khách hàng.

Chúng ta tạo file model định nghĩa cấu trúc dữ liệu về một khách hàng. Đối tượng này sẽ được sử dụng trong file Class Component.

{% highlight javascript  linenos %}

export class Customer {
 
  customerNo: number;
  name:string ;
  address:string;
  city:string;
  state:string;
  country:string;
 
}
{% endhighlight %}

Chúng ta sử dụng từ khoá export để các component khác có thể sử dụng được class component khách hàng của chúng ta. Nếu không có Angular sẽ báo lỗi khi sử dụng component khách hàng.

Sau khi chạy câu lệnh ng new Customer bằng Angular Cli. Nó sẽ tạo cho ta 1 folder tên customer ở dưới folder app. Trong folder này có các file để cấu hình 1 component. Chúng ta sẽ cấu hình theo từng bước như sau

- Bước 1 : Chỉnh sửa file customer.component.ts. Đây là file class component chứa data Customer ở trên. Chúng ta tạo sẳn 5 khách hàng

{% highlight javascript  linenos %}

import { Component } from '@angular/core';
import { Customer } from './customer';
 
@Component({
  selector: 'customer-list',
  templateUrl: './customer-list.component.html'
})
export class CustomerListComponent
{
  customers: Customer[] = [
 
    {customerNo: 1, name: 'Rahuld Dravid', address: '', city: 'Banglaore', state: 'Karnataka', country: 'India'},
    {customerNo: 2, name: 'Sachin Tendulkar', address: '', city: 'Mumbai', state: 'Maharastra', country: 'India'},
    {customerNo: 3, name: 'Saurrav Ganguly', address: '', city: 'Kolkata', state: 'West Bengal', country: 'India'},
    {customerNo: 4, name: 'Mahendra Singh Dhoni', address: '', city: 'Ranchi', state: 'Bihar', country: 'India'},
    {customerNo: 5, name: 'Virat Kohli', address: '', city: 'Delhi', state: 'Delhi', country: 'India'},
 
  ]
}
{% endhighlight %}

Đầu tiền chúng ta import các module cần thiết của angular và import thêm model customer vào để sử dụng

{% highlight javascript  linenos %}

import { Component } from '@angular/core';
import { Customer } from './customer'; 

{% endhighlight %}

Tiếp đến chúng ta thêm meta data là @Component cho class component. Chúng ta mô tả các thành phần trong @Component như selector tên gì, tìm kiếm file html template ở đâu

{% highlight javascript  linenos %}

@Component({
  selector: 'customer-list',
  templateUrl: './customer.component.html'
})

{% endhighlight %}

- Bước 2 : Tạo file template html(view) để hiển thị kết quả. file này ta có tên giống như tên trong templateUrl là customer.component.html. Chúng ta sẽ hiển thị danh sách 5 khách hàng

{% highlight html  linenos %}

<h2>List of Customers</h2>
 
<table class='table'>
  <thead>
    <tr>
      <th>No</th>
      <th>Name</th>
      <th>Address</th>
      <th>City</th>
      <th>State</th>
    </tr>
  </thead>
  <tbody>
    <tr *ngFor="let customer of customers;">
      <td>{{customer.customerNo}}</td>
      <td>{{customer.name}}</td>
      <td>{{customer.address}}</td>
      <td>{{customer.city}}</td>
      <td>{{customer.state}}</td>
    </tr>
  </tbody>
</table>

{% endhighlight %}

- Bước 3 : Như vậy component khách hàng chúng ta đã sẳn sàng. Chúng ta cần phải khai báo nó trong app.module.ts để sử dụng

{% highlight html  linenos %}

import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
 
import {NgbModule} from '@ng-bootstrap/ng-bootstrap';
 
import { AppComponent } from './app.component';
import {CustomerComponent} from './customer-list.component';
 
@NgModule({
  declarations: [
    AppComponent, CustomerComponent
  ],
  imports: [
    BrowserModule,NgbModule.forRoot()
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }

{% endhighlight %}

Đầu tiên chúng ta import Customer component vào 

{% highlight html  linenos %}

import {CustomerComponent} from './customer-list.component';

{% endhighlight %}

Sau đó khai báo nó trong Angular module

{% highlight html  linenos %}

@NgModule({
declarations: [
   AppComponent, CustomerListComponent
]

{% endhighlight %}

- Bước 4 : Nhúng component khách hàng vào component cha. Anh ví dụ mình có component cha là app.component.html giờ ta muốn nhúng component khách hàng vào trong component cha là app component ta làm như sau

{% highlight html  linenos %}

<h1>Danh sách khách hàng </h1>
 
<customer-list></customer-list>

{% endhighlight %}

- Trong file app.component.html ta sử dụng thẻ <customer-list>. Cái này ta định nghĩa ở thẻ selector trong component class mà ta làm ở bước 1.

{% highlight javascript  linenos %}

@Component({
  selector: 'customer-list',
  templateUrl: './customer.component.html'
})

{% endhighlight %}



























