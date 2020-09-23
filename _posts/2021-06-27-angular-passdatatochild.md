---
layout: course-angular
title: Truyền dữ liệu cho component con 
slug : angular-pass-data-to-child-component
category: laptrinhweb
tags: [angular]
summery: Truyền data cho component con  
image: /images/blog/angular.png
description : Truyền dữ liệu từ component cha xuống component con trong dự án angular. Hướng dẫn cách truyền dữ liệu từ cha xuống con  trong dự án Angular. 
youtubeId: 0734nF0B_BM
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người cách  <b>truyền dữ liệu từ component cha xuống con</b> là như thế nào? 

# **1.Truyền dữ liệu từ cha xuống con là gì**

Trong Angular để truyền dữ liệu từ component cha xuống các component con thì ta sử dụng annotaion @Input 

Trong dự án Angular component cha sẽ giao tiếp với component con thông qua thuộc tính properties. Annotation @Input được sử dụng để nhận các giá trị từ properties từ cha xuống con.

# **2.Ví dụ truyền dữ liệu từ cha xuống con**

Trong ví dụ hôm nay chúng ta sẽ truyền giá trị từ component cha xuống con. Giá trị ta truyền xuống là biến đếm (count) sẽ được truyền từ component cha xuống component con để hiển thị.

- Bước 1.  Ta có component con hiển thị biến count từ component cha truyền xuống như sau.

{% highlight javascript linenos %}

import { Component, Input  } from '@angular/core';
 
@Component({
    selector: 'child-component',
    template: '<h2>Child Component</h2>
               current count is {{ count }}'
})
export class ChildComponent {
    @Input() count: number;
}

{% endhighlight %} 

Đầu tiên chúng ta import annotation @Input từ thư viện angular core

{% highlight javascript linenos %}

import { Component, Input  } from '@angular/core';

{% endhighlight %} 

Chúng ta định nghĩa template html cho component. Chúng ta viết template html inline nên không cần phải tạo file html cho ví dụ này.

{% highlight javascript linenos %}

selector: 'child-component',
    template: '<h2>Child Component</h2>
               current count is {{ count }}'

{% endhighlight %} 

Biến count sẽ được truyền từ component cha xuống để component con có thể hiển thị. Để nhận được giá trị của biến count từ cha. Thì component con sẽ khai báo annotation @Input count với mục đích là sẽ nhận biến count từ cha truyền xuống.

{% highlight javascript linenos %}

export class ChildComponent {
    @Input() count: number;
}

{% endhighlight %} 

- Bước 2 : Từ component cha ta sẽ truyền giá trị count xuống component con thông qua thuộc tính  <child-component [count]=Counter></child-component>. Code của lớp cha như sau

{% highlight javascript linenos %}

import { Component} from '@angular/core';
 
@Component({
  selector: 'app-root',
  template: '
        <h1>Welcome to {{title}}!</h1>
        <button (click)="increment()">Increment</button>
        <button (click)="decrement()">decrement</button>
        <child-component [count]=Counter></child-component>' ,
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'Component Interaction';
  Counter = 5;
 
  increment() {
    this.Counter++;
  }
  decrement() {
    this.Counter--;
  }
}
{% endhighlight %} 


Trong component cha ta có 2 buttons dùng để tăng và giảm giá trị của biến count.

{% highlight javascript linenos %}

 <button (click)="increment()">Increment</button>
 <button (click)="decrement()">decrement</button>

{% endhighlight %} 

Dòng tiếp theo ta nhúng component con vào component cha thông qua thẻ child-component. Đồng thời truyền giá trị count qua cho component con thông qua thuộc tính [count] = Counter


{% highlight javascript linenos %}

<child-component [count]=Counter></child-component>

{% endhighlight %} 

# **3. Truyền dữ liệu từ cha xuống con thống qua component**

Ngoài cách nhận dữ liệu bằng cách sử dụng annotation @input ở trên

{% highlight javascript linenos %}

export class ChildComponent {
     @Input() count: number;
}

{% endhighlight %}

Ta có thể khai báo input trong thẻ component meta data vẫn có kết quả như nhau. Ví dụ đoạn code sau

{% highlight javascript linenos %}

@Component({
    selector: 'child-component',
    inputs: ['count'],
    template: '<h2>Child Component</h2>
    current count is {{ count }}'
})
export class ChildComponent {}

{% endhighlight %}

# **4. Đặt tên cho thuộc tính truyền từ cha xuống con**

Chúng ta có thể đặt tên biến count là MyCount như sau trong component class của lớp con

{% highlight javascript linenos %}

export class ChildComponent {
     @Input('MyCount') count: number;
}

{% endhighlight %}

Sau đó ở lớp cha ta truyền xuống bằng tên của Input như sau

{% highlight html linenos %}

<h1>Welcome to {{title}}!</h1>
<child-component [MyCount]=ClickCounter></child-component>

{% endhighlight %}

# **5. Phát hiện khi nào có sự thay đổi từ cha**

Ngoài việc truyền data từ component cha xuống cho con. Thì lớp còn cần phải biết thêm khi nào giá trị của lớp cha thay đổi để nó có thể cập nhật lại. Có 2 cách để có thể phát hiện ra khi input thay đổi là

- Sử dụng phương thức OnChanges trong vòng đời của một component
- Sử dụng Setter

# **6. Sử dụng OnChange**

ngOnChanges được dùng để Angular phát hiện ra khi nào giá trị thay đổi. Chúng ta sẽ cập nhật thêm component con phương thức ngOnChanges() để khi component cha thay đổi giá trị thì component con sẽ cập nhật giá trị

{% highlight javascript linenos %}

import { Component, Input, OnChanges, SimpleChanges, SimpleChange  } from '@angular/core';
 
@Component({
    selector: 'child-component',
    template: '<h2>Child Component</h2>
               current count is {{ count }}'
})
export class ChildComponent implements OnChanges {
    @Input() count: number;
 
    ngOnChanges(changes: SimpleChanges) {
 
        for (let property in changes) {
            if (property === 'count') {
              console.log('Previous:', changes[property].previousValue);
              console.log('Current:', changes[property].currentValue);
              console.log('firstChange:', changes[property].firstChange);
            } 
        }
    }
}
{% endhighlight %}

Đầu tiên chúng ta import các thư việc cần vào

{% highlight javascript linenos %}

import { Component, Input, OnChanges, SimpleChanges, SimpleChange  } from '@angular/core';
 
{% endhighlight %}

Tiếp đến chúng ta thay thêm class OnChanges vào

{% highlight javascript linenos %}

export class ChildComponent implements OnChanges {
 
{% endhighlight %}

Chúng ta viết thêm method ngOnChanges

{% highlight javascript linenos %}

ngOnChanges(changes: SimpleChanges) {
 
        for (let property in changes) {
            if (property === 'count') {
              console.log('Previous:', changes[property].previousValue);
              console.log('Current:', changes[property].currentValue);
              console.log('firstChange:', changes[property].firstChange);
            } 
        }
    }
 
{% endhighlight %}

Method ngOnchanges sẽ nhận được các sự thay đổi trên properties của component cha và chuyển đổi nó thành object SimpleChanges. Đối tượng SimpleChanges chứa đựng key là tên của thuộc tính và giá trị là đối tượng SimpleChanges. Có được đối tượng SimpleChanges ta có thể lấy được giá trị hiện tại, giá trị trước khi thay đổi. Từ đó ta sẽ cập nhật lại giao diện dựa trên các giá trị ta có.

# **7. Sử dụng Input Setter**

Chúng ta có thể sử dụng getter và setter để phát hiện ra sự thay đổi.

Trong component con ta tạo một biến tên count

{% highlight javascript linenos %}

private count = 0;

{% endhighlight %}

Chúng ta tạo getter và setter cho biến count và thêm annotation @Input trên phương thức như sau

{% highlight javascript linenos %}

@Input()
set count(count: number) {
    this.count = count;
    console.log(count);
}
get count(): number { return this.count; }

{% endhighlight %}











