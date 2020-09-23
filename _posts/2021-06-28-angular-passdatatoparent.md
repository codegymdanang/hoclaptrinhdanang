---
layout: course-angular
title: Truyền dữ liệu từ component con lên cha 
slug : angular-pass-data-from-child-to-parent-component
category: laptrinhweb
tags: [angular]
summery: Truyền data từ component con lên cha  
image: /images/blog/angular.png
description : Truyền dữ liệu từ component con lên component cha trong dự án angular. Hướng dẫn cách truyền dữ liệu từ component con lên component cha  trong dự án Angular. 
youtubeId: 0734nF0B_BM
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người cách  <b>component con lên component cha</b> là như thế nào? 

# **1.Truyền dữ liệu từ component con lên component cha**

Chúng ta có 3 cách để truyền dữ liệu lên component cha từ component con. Chúng ta sẽ lần luợt đi qua các cách.

# **2.Ví dụ truyền dữ liệu từ con lên cha qua sự kiện**

Trong ví dụ sau ta sẽ truyền giá trị từ component con qua component cha thông qua sự kiện. Trong component con ta sẽ sử dụng EventBinding để lắng nghe sự thay đổi data từ component con.

Ta có component con tên child.component.ts như sau

{% highlight javascript linenos %}

import { Component, Input, Output, EventEmitter  } from '@angular/core';
 
@Component({
    selector: 'child-component',
    template: '<h2>Child Component</h2>
               <button (click)="increment()">Increment</button>
               <button (click)="decrement()">decrement</button>
               current count is {{ count }}'
})
export class ChildComponent {
    @Input() count: number;
 
    @Output() countChanged: EventEmitter<number> =   new EventEmitter();
 
    increment() {
        this.count++;
        this.countChanged.emit(this.count);
      }
    decrement() {
        this.count--;
        this.countChanged.emit(this.count);
    }
}

{% endhighlight %} 

Đầu tiên chúng ta import thư việc output và EventEmitter từ angular core

{% highlight javascript linenos %}

import { Component, Input, Output, EventEmitter } from '@angular/core';

{% endhighlight %}

Trong file template html ta có 2 nút buttons dùng để tăng và giảm biến count

{% highlight javascript linenos %}

@Component({
    selector: 'child-component',
    template: '<h2>Child Component</h2>
               <button (click)="increment()">Increment</button>
               <button (click)="decrement()">decrement</button>
               current count is {{ count }}'
})

{% endhighlight %}

Trong component con chúng ta định nghĩa sự kiện countChange là loại EventEmitter và đặt cho nó annotation @Output để component cha có thể làm việc được với component con và để component cha thấy được sự kiện phát sinh từ component con

{% highlight javascript linenos %}

@Output() countChanged: EventEmitter<number> = new EventEmitter();

{% endhighlight %}

Cuối cùng component con phát sinh sự kiện lên cho cha thông qua phương thức emit

{% highlight javascript linenos %}

increment() {
        this.count++;
        this.countChanged.emit(this.count);
      }
    decrement() {
        this.count--;
        this.countChanged.emit(this.count);
    }

{% endhighlight %}

Trong Parent component chúng ta bắt lại sự kiện từ component con và sử lý như sau

{% highlight html linenos %}

<child-component [count]=ClickCounter (countChanged)='countChangedHandler($event)'>
</child-component>
    
{% endhighlight %}

Trong component cha ta viết hàm countChangedHandler để xử lý sự kiện từ component con

{% highlight javascript linenos %}

countChangedHandler(count: number) {
    this.ClickCounter = count;
    console.log(count);
  }
{% endhighlight %}

# **3.Ví dụ truyền dữ liệu từ con lên cha qua biến cục bộ**

Chúng ta có lớp component con như sau. Chúng ta xoá đi input, output và event emitter

{% highlight javascript linenos %}

import { Component} from '@angular/core';
 
@Component({
    selector: 'child-component',
    template: '<h2>Child Component</h2>
               current count is {{ count }}'
})
export class ChildComponent {
    count = 0;
 
     increment() {
        this.count++;
      }
    decrement() {
        this.count--;
    }
}

{% endhighlight %}

Chúng ta có component cha như sau

{% highlight javascript linenos %}

import { Component} from '@angular/core';
 
@Component({
  selector: 'app-root',
  template: '
        <h1>{{title}}!</h1>
        <p> current count is {{child.count}} </p>
        <button (click)="child.increment()">Increment</button>
        <button (click)="child.decrement()">decrement</button>
        <child-component #child></child-component>' ,
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'Parent interacts with child via local variable';
}

{% endhighlight %}

Chúng ta tạo biến tên #child trong thẻ child-component. Biến này còn được gọi là biến template. Nó sẽ được hiển thị ở component con

{% highlight javascript linenos %}

<child-component #child></child-component>

{% endhighlight %}

Bầy giờ chúng ta sử dụng biến local template child để gọi các method và thuộc tính trong component con

{% highlight javascript linenos %}

  <button (click)="child.increment()">Increment</button>
  <button (click)="child.decrement()">decrement</button>

{% endhighlight %}

# **4.Ví dụ truyền dữ liệu từ con lên cha qua ViewChild**

Chúng ta có thể nhúng instance của component con vào cha thông qua annotation @ViewChild. Dựa vào ViewChild component cha có thể gọi được các phương thức và thuộc tính của component cha.

Ví du ta có component cha như sau

{% highlight javascript linenos %}

import { Component, ViewChild } from '@angular/core';
import { ChildComponent } from './child.component';
 
@Component({
  selector: 'app-root',
  template: '
        <h1>{{title}}</h1>
        <p> current count is {{child.count}} </p>
        <button (click)="increment()">Increment</button>
        <button (click)="decrement()">decrement</button>
        <child-component></child-component>' ,
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'Parent calls an @ViewChild()';
 
  @ViewChild(ChildComponent) child: ChildComponent;
 
  increment() {
    this.child.increment();
  }
 
  decrement() {
    this.child.decrement();
  }
}
 

{% endhighlight %}


Đầu tiên ta import ViewChild từ angular core

{% highlight javascript linenos %}

import { Component, ViewChild } from '@angular/core';

{% endhighlight %}

Tiếp đến chúng ta tạo biên ViewChild và annotation là @ViewChild

{% highlight javascript linenos %}

@ViewChild(ChildComponent) child: ChildComponent;

{% endhighlight %}

Cuối cùng ta add thêm phương thức increment và decrement. Các phương thức này sẽ gọi hàm increase và decrement từ component con

{% highlight javascript linenos %}

increment() {
    this.child.increment();
  }
 
  decrement() {
    this.child.decrement();
  }
{% endhighlight %}





