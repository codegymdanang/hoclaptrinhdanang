---
layout: course-angular
title: Sử dụng Directive ngClass
slug : angular-ngClass
category: laptrinhweb
tags: [angular]
summery: NgClass 
image: /images/blog/angular.png
description : Thêm NgClass trong dự án angular. Hướng dẫn sử dụng NgClass vào dự án Angular. Hướng dẫn các tạo NgClass vào dự án.
youtubeId: 0734nF0B_BM
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người cách tạo <b>ngClass</b> là như thế nào? 

# **1. ngClass là gì**

Chúng ta sử dụng ngClass để thêm hay xoá một css trong phần tử html.

- Cú pháp ngIf như sau

{% highlight html  linenos %}

<element [ngClass]="expression">...</element>

{% endhighlight %}

- element : chính là phần tử của web
- expression : điều kiện và css được thêm vào


# **2. Ví dụ ngClass**

Ví dụ ta có một số thuộc tính css được định nghĩa trong file component app.component.css như sau

{% highlight css  linenos %}

.red { color: red; }
.size20 { font-size: 20px; }

{% endhighlight %}


Tiếp đến ta sẽ sử dụng nó trong file template html như sau

{% highlight html  linenos %}

<div [ngClass]="'red size20'"> Red Text with Size 20px </div>

{% endhighlight %}

# **3. ngClass với mảng**

Chúng ta có thể khai báo dạng mảng css trong file template html như sau

{% highlight html  linenos %}

<div [ngClass]="['red','size20']">Red Text with Size 20px </div>

{% endhighlight %}

# **4. Cập nhật giá trị css động**

Ví dụ trong file component class ta có biến cssStringVar. Sau đó ta gán nó qua bên template html, như vậy khi giá trị cssStringVar thay đổi thì nó sẽ cập nhật giá trị đó bên template html

- Ta có file component class như sau

{% highlight javascript  linenos %}

cssStringVar: string= 'red size20';

{% endhighlight %}

- Ta sẽ binding giá trị cssStringVar qua file template

{% highlight html  linenos %}

<div class="row">     
   <div [ngClass]="cssStringVar">Red Text with Size 20px : from component     </div> 
</div>

{% endhighlight %}

# **5. Cập nhật giá trị css động với array**

{% highlight javascript  linenos %}

cssArray:string[]=['red','size20']; 

{% endhighlight %}

- Ta sẽ binding giá trị cssArray qua file template

{% highlight html  linenos %}

<div class="row">
  <div [ngClass]="cssArray">
    Red Text with Size 20px  : from CSS Array
  </div>
</div>

{% endhighlight %}

# **6. Cập nhật giá trị css động với đối tượng**

- Ví dụ ta có class tên là CssClass

{% highlight javascript  linenos %}

class CssClass {
  red: boolean= true;
  size20: boolean= true; 
}

{% endhighlight %}

- Trong file component class ta tạo đối tượng CssClass

{% highlight javascript  linenos %}

cssClass: CssClass = new CssClass();

{% endhighlight %}

- Ta truyền qua file template html

{% highlight html  linenos %}

<div class="row">     
  <div [ngClass]="cssClass"> Red Text with Size 20px : from component as object</div> 
</div>

{% endhighlight %}









