---
layout: course-angular
title: Vòng đời của component trong Agule 
slug : angular-lifecycle
category: laptrinhweb
tags: [angular]
summery: Vòng đời của component
image: /images/blog/angular.png
description : Vòng đời của component trong dự án angular. Hướng dẫn vòng đời của component  trong dự án Angular. 
youtubeId: 0734nF0B_BM
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>Vòng đời của component</b> trong Angular là như thế nào? 

# **1.Vòng đời của component**

Vòng đời của một component hay một directive trong Angular tính từ lúc nó được tạo ra, nó bị thay đổi và bị phá huỷ. Hiểu được vòng đời của component ta có thể viết code can thiệp trong quá trình component hay direct được tạo ra, được cập nhật và phá huỷ.

Khi ứng dụng Angular được start lên thì đầu tiên nó sẽ tạo và render component cha (hay còn gọi là root component) sau đó nó sẽ tạo và render các component con. Khi mỗi component được load lên, component sẽ kiểm tra xem có data binding vào nó không, dữ liệu có thay đổi không và cập nhật lại chúng. Khi component bị phá huỷ thì chúng sẽ bị remove (xoá) khỏi giao diện web 

Angular cung cấp cho chúng ta một số phương thức về vòng đời của một component. Dựa vào đó chúng ta có thể can thiệp vào quá trình tạo ra component, cập nhật giá trị và phá huỷ của component. Sau đây là thứ tự từ trên xuống dưới về các method sẽ được sử dụng trong vòng đời của một component.

- ngOnChanges
- ngOnInit
- ngDoCheck
- ngAfterContentInit
- ngAfterContentChecked
- ngAfterViewInit
- ngAfterViewChecked
- ngOnDestroy

# **1. ngOnChanges**

Phương thức ngOnChanges được gọi khi component phát hiện có giá trị được binding vào component băng phương pháp Input properties. Để nhận biết được giá trị binding thì ngOnChange quản lý đối tượng SimpleChanege. Chúng ta sử dụng @Input trong bài truyền giá trị từ cha xuống con là một ví dụ

Ví dụ sau ta có component cha truyền giá trị message xuống cho component con (child-component) thông qua properties sau đó component con sẽ dùng @Input để nhận giá trị và binding vào component

{% highlight javascript linenos %}

import { Component} from '@angular/core';
import { Customer } from './customer';
 
@Component({
  selector: 'app-root',
  template: '
        <h1>{{title}}!</h1>
        <p> Message : <input type='text' [(ngModel)]='message'> </p>
        <p> Code : <input type='text' [(ngModel)]='code'></p>
        <p> Name : <input type='text' [(ngModel)]='name'></p>
        <p><button (click)="updateCustomer()">Update </button>
        <child-component [message]=message [customer]=customer></child-component>
        ' ,
 
        styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'ngOnChanges';
  message = '';
  customer: Customer = new Customer();
  name= '';
  code= 0;
 
  updateCustomer() {
    this.customer= new Customer();
    this.customer.name = this.name;
    this.customer.code = this.code;
  }
 
}

{% endhighlight %} 

Chúng ta có component con với nội dung nhu sau

{% highlight javascript linenos %}

import { Component, Input, OnInit, OnChanges, SimpleChanges, SimpleChange,ChangeDetectionStrategy  } from '@angular/core';
import { Customer } from './customer';
 
@Component({
    selector: 'child-component',
    template: '<h2>Child  Component</h2>
               <p>Message {{ message }} </p>
               <p>Customer Name {{ customer.name }} </p>
               <p>Customer Code {{ customer.code }} <p>
               <ul><li *ngFor="let log of changelog;"> {{ log }}</li></ul> '
})
export class ChildComponent implements OnChanges, OnInit {
    @Input() message: string;
    @Input() customer: Customer;
    changelog: string[] = [];
 
    ngOnInit() {
        console.log('OnInit');
    }
 
    ngOnChanges(changes: SimpleChanges) {
        console.log('OnChanges');
        console.log(JSON.stringify(changes));
 
        // tslint:disable-next-line:forin
        for (const propName in changes) {
             const change = changes[propName];
             const to  = JSON.stringify(change.currentValue);
             const from = JSON.stringify(change.previousValue);
             const changeLog = `${propName}: changed from ${from} to ${to} `;
             this.changelog.push(changeLog);
        }
    }
}
{% endhighlight %} 

Đầu tiên chúng ta import thư viện từ angular core như sau

{% highlight javascript linenos %}

import { Component, Input, OnInit, OnChanges, SimpleChanges, SimpleChange } from '@angular/core';

{% endhighlight %} 

Tiếp đến ta cài đặt các vòng đời của Angular

{% highlight javascript linenos %}

export class ChildComponent implements OnChanges, OnInit {
    @Input() message: string;
    @Input() customer: Customer;
    changelog: string[] = [];
{% endhighlight %} 

Trong hàm ngOnChnages ta lấy tất cả các sự thay đổi giá trị của component thông qua đối tượng SimpleChange

{% highlight javascript linenos %}

ngOnChanges(changes: SimpleChanges) {
        console.log('OnChanges');
        console.log(JSON.stringify(changes));

{% endhighlight %} 

Xử lý nghiệp vụ trong hàm ngOnChange cho phù hợp với yêu cầu của chúng ta.


# **2. ngOninit**

Phương thức NgOninit được gọi, khi component được tạo lần đầu tiên. Chúng ta được chạy  sau khi hàm constructor và hàm ngOnchange được thực hiện.

{% highlight javascript linenos %}

import { Component,  OnInit } from '@angular/core';
 
@Component({
  selector: 'child-component',
  template: '
      <h2>Child Component</h2>
      ' ,
  styleUrls: ['./app.component.css']
})
export class ChildComponent implements OnInit {
 
  constructor() {
    console.log('ChildComponent:Constructor');
  }
 
  ngOnInit() {
    console.log('ChildComponent:OnInit');
  }
 }

{% endhighlight %} 

Đầu tiên chúng ta import thư viện OnInit từ angular core

{% highlight javascript linenos %}

import { Component, OnDestroy, OnInit } from '@angular/core';

{% endhighlight %} 

Tiếp đến chúng ta khai báo cài đặt hàm OnInit

{% highlight javascript linenos %}

export class ChildComponent implements OnInit {

{% endhighlight %} 

Cuối cùng chúng ta viết code trong phương thức ngOnInit để can thiệt vào lúc component được tạo ra

{% highlight javascript linenos %}

ngOnInit() {
  console.log('ChildComponent:OnInit');
}

{% endhighlight %} 

# **3. ngOnDoCheck**

Phương thức ngOnDoCheck được gọi mỗi khi nó phát hiện ra có sự thay đổi dữ liệu ở component.

{% highlight javascript linenos %}

import { Component, Input, OnChanges, OnInit, SimpleChanges, SimpleChange, DoCheck  } from '@angular/core';
import { Customer } from './customer';
 
@Component({
    selector: 'child-component',
    template: `<h2>Child  Component</h2>
               <p>Message {{ message }} </p>
               <p>Customer Name {{ customer.name }} </p>
               <p>Customer Code {{ customer.code }} </p>
               <p>Do Check count {{ DocheckCount }} </p>
               <ul><li *ngFor="let log of changelog;"> {{ log }}</li></ul> `
})
export class ChildComponent implements OnChanges, DoCheck, OnInit {
    @Input() message: string;
    @Input() customer: Customer;
    changelog: string[] = [];
    oldCustomer: Customer= new Customer();
    DocheckCount = 0;
 
    ngOnInit() {
        console.log('OnInit');
        this.oldCustomer = Object.assign({}, this.customer);
    }
 
    ngDoCheck() {
        console.log('Docheck');
        this.DocheckCount++;
        if (this.oldCustomer.name !== this.customer.name || this.oldCustomer.code !== this.customer.code ) {
            const to  = JSON.stringify(this.customer);
            const from = JSON.stringify(this.oldCustomer);
            const changeLog = `DoCheck customer: changed from ${from} to ${to} `;
            this.changelog.push(changeLog);
 
            this.oldCustomer = Object.assign({}, this.customer);
        }
    }
 
    ngOnChanges(changes: SimpleChanges) {
        console.log('OnChanges');
        console.log(JSON.stringify(changes));
 
        // tslint:disable-next-line:forin
        for (const propName in changes) {
             const change = changes[propName];
             const to  = JSON.stringify(change.currentValue);
             const from = JSON.stringify(change.previousValue);
             const changeLog = `${propName}: changed from ${from} to ${to} `;
             this.changelog.push(changeLog);
        }
    }
{% endhighlight %} 

Đầu tiên chúng ta import DoCheck từ thư viện angular core 

{% highlight javascript linenos %}

import { Component, Input, OnChanges, OnInit, SimpleChanges, SimpleChange, DoCheck  } from '@angular/core';

{% endhighlight %} 

Chúng ta implement DoCheck interface

{% highlight javascript linenos %}

export class ChildComponent implements OnChanges, DoCheck, OnInit {

{% endhighlight %} 

Cuối cùng chúng ta viết code trong hàm ngDoCheck để kiểm tra sự thay đổi và thêm các dòng code mình muốn

{% highlight javascript linenos %}
ngDoCheck() {
        console.log('Docheck');
        this.DocheckCount++;
        if (this.oldCustomer.name !== this.customer.name || this.oldCustomer.code !== this.customer.code ) {
            const to  = JSON.stringify(this.customer);
            const from = JSON.stringify(this.oldCustomer);
            const changeLog = `DoCheck customer: changed from ${from} to ${to} `;
            this.changelog.push(changeLog);
 
            this.oldCustomer = Object.assign({}, this.customer);
        }
{% endhighlight %} 

# **4. ngAfterContentInit**

Phương thức này được gọi sau khi component được khởi tạo thành công

{% highlight javascript linenos %}

@Component({selector: 'my-cmp', template: `...`})
class MyComponent implements AfterContentInit {
  ngAfterContentInit() {
    // ...
  }
}
{% endhighlight %} 

# **5. ngAfterContentChecked**

{% highlight javascript linenos %}

Phương thức này được gọi sau khi Component Content được kiểm tra bởi Angular's Change module.

@Component({selector: 'my-cmp', template: `...`})
class MyComponent implements AfterContentChecked {
  ngAfterContentChecked() {
    // ...
  }
}
{% endhighlight %} 

# **6. ngAfterViewInit**

Nó tượng tự nhưg ngAfterContentInit but nó được gọi khi component và các component con của nó được khởi tạo thành công. Chỉ được gọi 1 lần sau khi ngAfterContentChecked 

{% highlight javascript linenos %}

@Component({selector: 'my-cmp', template: `...`})
class MyComponent implements AfterViewInit {
  ngAfterViewInit() {
    // ...
  }
}
{% endhighlight %} 

# **7. ngAfterViewChecked**

Phương thức này được gọi sau khi các view component cha  và các view của component con được kiểm tra xong.

{% highlight javascript linenos %}

@Component({selector: 'my-cmp', template: `...`})
class MyComponent implements AfterViewChecked {
  ngAfterViewChecked() {
    // ...
  }
}
{% endhighlight %} 

# **8. ngOnDestroy**

Phương thức ngOnDestroy được gọi trước khi component hoặc directive bị phá huỷ bởi Angular

{% highlight javascript linenos %}

import { Component, OnDestroy } from '@angular/core';
 
@Component({
  selector: 'child-component',
  template: '
      <h2>Child Component</h2>
      ',
  styleUrls: ['./app.component.css']
})
export class ChildComponent implements OnDestroy {
 
  constructor() {
    console.log('ChildComponent:Constructor');
  }
 
 
 
  ngOnDestroy() {
    console.log('ChildComponent:OnDestroy');
  }
 
}

{% endhighlight %} 

Đầu tiên chúng ta import OnDestroy tử angular core

{% highlight javascript linenos %}

import { Component, OnDestroy } from '@angular/core';

{% endhighlight %} 

Tiếp đến implement OnDestroy Interface

{% highlight javascript linenos %}

export class ChildComponent implements OnDestroy

{% endhighlight %} 

Cuối cùng là viết code trong hàm ngOnDestroy

{% highlight javascript linenos %}

ngOnDestroy() {
    console.log('ChildComponent:OnDestroy');
  }
{% endhighlight %} 








