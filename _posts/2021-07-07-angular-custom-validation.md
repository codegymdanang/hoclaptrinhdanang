---
layout: course-angular
title: Custom Validation  
slug : angular-custom-validation
category: laptrinhweb
tags: [angular]
summery: Custom Validation   
image: /images/blog/angular.png
description : Sử dụng Custom Validation trong dự án angular. Hướng dẫn cài đặt Custom Validation vào dự án Angular. Hướng dẫn các tạo một ứng dụng Custom Validation.
youtubeId: 
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người cách <b>Custom Validation</b> là như thế nào?

# **1.Custom Validation là gì**

Angular hỗ trợ một số validator như required, min length, max length, pattern và email như ta đã xem ở bài trước. Ngoài những validator có sẳn của Angular ta hoàn toàn có thể tự tạo một validator cho dự án của mình.


# **2.Sử dụng Validator như thế nào**

Giả sử ta có form trong file template html như sau.

{% highlight javascript linenos %}

<h1>Custom Validator in Angular</h1>
 
<h2>Reactive Form</h2>
 
<form [formGroup]="myForm" (ngSubmit)="onSubmit()" novalidate>
 
  <div>
    <label for="numVal">Number :</label>
    <input type="text" id="numVal" name="numVal" formControlName="numVal">
  </div>
 
  <p>Is Form Valid : {{myForm.valid}} </p>
 
  <p>
    <button type="submit" [disabled]="!myForm.valid">Submit</button>
  </p>
 
</form>

{% endhighlight %} 

Như các em thấy ta có 1 field trong form là numVal. Chúng ta muốn giá trị trong numVal phải lớn hơn 10.

Bây giờ ta sẽ định nghĩa một Validator riêng cho việc kiểm tra giá trị lớn hơn 10. Ta tạo một file gte.validator.js như sau

{% highlight javascript linenos %}

import { AbstractControl, ValidationErrors } from '@angular/forms'
 
export function gte(control: AbstractControl): ValidationErrors | null {
 
    const v=+control.value;
 
    if (isNaN(v)) {
      return { 'gte': true, 'requiredValue': 10 }
    }      
 
    if (v <= 10) {
      return { 'gte': true, 'requiredValue': 10 }
    } 
 
    return null
 
}

{% endhighlight %} 

Đầu tiên chúng ta import thư viện AbstractControl và Validation Error từ Angular Form

{% highlight javascript linenos %}

import { AbstractControl, ValidationErrors } from '@angular/forms'

{% endhighlight %} 

ValidatorError chức cặp key và value. Key là tên của rule chúng ta muốn sử dụng và value có thể làm bất cứ cái gì.

Trong ví dụ sau chúng ta kiểu tra giá trị của control có phải là số hay không. Để kiểm tra số ta dùng hàm isNaN. Đồng thời kiểm tra giá trị nhỏ hơn hay bằng 10. Nếu cả 2 điều kiện là đúng thì trả về null.

{% highlight javascript linenos %}

const v=+control.value;
 
    if (isNaN(v)) {
      return { 'gte': true, 'requiredValue': 10 }
    }      
 
    if (v <= 10) {
      return { 'gte': true, 'requiredValue': 10 }
    } 
 
    return null
{% endhighlight %} 

Nếu validator bị sai thì trả về Validator Error

{% highlight javascript linenos %}

return { 'gte': true, 'requiredValue': 10 }

{% endhighlight %}

Để sử dụng Custom validator chúng ta import vào component class

{% highlight javascript linenos %}

import { gte } from './gte.validator';

{% endhighlight %}

Thêm validator vào form như sau


{% highlight javascript linenos %}

 myForm = new FormGroup({
    numVal: new FormControl('', [gte]),
  })
{% endhighlight %}

# **3. Code hoàn chỉnh cho component class**

{% highlight javascript linenos %}

import { Component } from '@angular/core';
import { FormGroup, FormControl, AbstractControl, ValidationErrors } from '@angular/forms'
import { gte } from './gte.validator';
 
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
 
  constructor() {
  }
 
  myForm = new FormGroup({
    numVal: new FormControl('', [gte]),
  })
 
  get numVal() {
    return this.myForm.get('numVal');
  }
 
  onSubmit() {
    console.log(this.myForm.value);
  }
}
{% endhighlight %}

# **4. Code hoàn chỉnh cho template html**

{% highlight javascript linenos %}

 <div>
    <label for="numVal">Number :</label>
    <input type="text" id="numVal" name="numVal" formControlName="numVal">
    <div *ngIf="!numVal.valid && (numVal.dirty ||numVal.touched)">
      <div *ngIf="numVal.errors.gte">
        The number should be greater than {{numVal.errors.requiredValue}}
      </div>
    </div>
 
  </div>
{% endhighlight %}


