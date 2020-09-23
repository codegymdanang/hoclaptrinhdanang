---
layout: course-angular
title: Angular Dependency Injection  
slug : angular-dependency-injection
category: laptrinhweb
tags: [angular]
summery: Dependency Injection   
image: /images/blog/angular.png
description : Sử dụng Dependency Injection trong dự án angular. Hướng dẫn cài đặt Dependency Injection vào dự án Angular.
youtubeId: dđ
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>Dependency Injection</b> là như thế nào?

# **1. Dependency Injection là gì**

Dependency Injection là một phần quan trọng trong bộ core của Angular. Sử dụng cơ chế Dependency Injection giúp chúng ta có thể nhúng service vào các component hoặc các service với nhau.

Như ta thấy ở ví dụ bài Service. Ta nhúng Service vào Component bằng cách tạo new đối tượng ProductService trong constructor như sau


{% highlight javascript linenos %}

import { Component } from '@angular/core';
 
import { ProductService } from './product.service';
import { Product } from './product';
 
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
})
 
export class AppComponent
{
 
   products:Product[];
   productService;
 
   constructor(){
     this.productService=new ProductService();
   }
 
   getProducts() {
     
     this.products=this.productService.getProducts();
   }
  
}

{% endhighlight %} 

Cách này có rất nhiều hạn chế mà anh nêu lên trong phần cuối của bài Service và thực tế thì không ai dùng cả. Như vậy ta phải thay đổi cách nhúng ServiceProduct vào Component theo cơ chế Dependency Injection 


# **2. Dependency Injection Framework**

Có 5 thành phần chính trong Angular Dependency Injection Framework

- Consumer : nơi mà nhúng service vào. Trong ví dụ của chúng ta là AppComponent

- Dependency : Những service được nhúng vào component

- DI Token : Được sinh ra là một dãy ký tự tượng trưng cho ID và là duy nhất khi Service đăng ký là Dependency Injection với Framework

- Provider : quản lý danh sách các dependencies và token của nó

- Injector : quản lý việc nhúng các đối tượng Dependency vào các consumer

Cơ chế hoạt động của Dependency như sau

- Dependency đăng ký với Provider

- Sau đó Angular Provider sẽ nhúng các dependecy vào các module consumer tương ứng.

- Consumer sẽ khởi tạo các đối tượng Dependency thông qua constructor.

Chúng ta sẽ viết lại ví dụ ProductService ở trên bằng cách sử dụng DI

{% highlight javascript linenos %}

import { Component } from '@angular/core';
 
import { ProductService } from './product.service';
import { Product } from './product';
 
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  providers: [ProductService]
})
export class AppComponent
{
 
   products:Product[];
   
   constructor(private productService:ProductService){
   }
   
   getProducts() {
     this.products=this.productService.getProducts();
   }
  
}
{% endhighlight %}

Chúng ta sẽ thêm thẻ provider trong @Component

{% highlight javascript linenos %}

 providers: [ProductService]

{% endhighlight %}

Trong Constructor chúng ta không tạo new đối tượng nữa và dùng

{% highlight javascript linenos %}

constructor(private productService:ProductService){
}

{% endhighlight %}  

# **2. Nhúng 1 Service vào 1 Service khác**

Trong ví dụ dưới đây ta sẽ nhúng Service Log vào Service Product. Service Log chỉ làm nhiệm vụ ghi log.

- Chúng ta tạo Logger Service

{% highlight javascript linenos %}

import { Injectable } from '@angular/core';
 
@Injectable()
export class LoggerService {
  log(message:any) {
    console.log(message);
  }
}

{% endhighlight %}  

Chúng ta sử dụng @Injectable cho những service nào mà chúng ta có ý định nhúng vào. Đây dạng như một quy định chung cho các service để chúng ta có thể phân biệt mục đích của các class. 

- Chúng ta tạo lớp ProductService

{% highlight javascript linenos %}

@Injectable()
export class ProductService{}

{% endhighlight %}  

- Trong constructor của ProductService chúng ta nhúng LogService vào

{% highlight javascript linenos %}

constructor(private loggerService: LoggerService) {
    this.loggerService.log("Product Service Constructed");
}

{% endhighlight %}  

- Chúng ta cập nhật phương thức getProduct của ProductService

{% highlight javascript linenos %}

public  getProducts() {
 
        this.loggerService.log("getProducts called");
        let products:Product[];
 
        products=[
            new Product(1,'Memory Card',500),
            new Product(1,'Pen Drive',750),
            new Product(1,'Power Bank',100)
        ]
 
        this.loggerService.log(products);
        return products;               
    }

{% endhighlight %}  

Cuối cùng chúng ta đăng ký Service Log và Product trong AppComponent

{% highlight javascript linenos %}

import { Component } from '@angular/core';
 
import { ProductService } from './product.service';
import { Product } from './product';
 
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  providers: [ProductService,LoggerService]
})

{% endhighlight %} 

# **3. Sử dụng ngModule để đăng ký dependency**

Ngoài cách đăng ký service trong thuộc tính providers trong Component. Chúng ta có thể đăng ký trong ngModule.

Để đảm bảo dependecy được nhúng vào toàn bộ ứng dụng Angular, chúng ta khai Provider ở root module.

Đầu tiên chúng ta xoá thuộc tính provider trong AppComponent


{% highlight javascript linenos %}

import { Component } from '@angular/core';
 
import { ProductService } from './product.service';
import { Product } from './product';
 
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html'
 
})

{% endhighlight %} 

Tiếp đến chúng ta khai báo provider trong ngModule của angular

{% highlight javascript linenos %}

import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { HttpModule } from '@angular/http';
import { FormsModule } from '@angular/forms';
 
import { AppComponent } from './app.component';
 
import { ProductService } from './product.service';
import { LoggerService } from './logger.service';
 
@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    HttpModule,
    FormsModule
  ],
  providers: [ProductService,LoggerService],
  bootstrap: [AppComponent]
})
export class AppModule { }

{% endhighlight %} 


Chúng ta sẽ thấy dòng Provider như sau

{% highlight javascript linenos %}

providers: [ProductService,LoggerService],

{% endhighlight %} 