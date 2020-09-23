---
layout: course-angular
title: Gọi webservice
slug : angular-call-webservice
category: laptrinhweb
tags: [angular]
summery: Angular gọi Webservice
image: /images/blog/angular.png
description : Hướng dẫn gọi webservice trong dự án Angular. Hiểu được cách gọi web service trong dự án angular. Hiểu được mục đích của thư viện HTTP Client được sử dụng như thế nào để gọi các webservices.
youtubeId: edYsCowgQq0
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người cách gọi <b>Web Service</b> bên ngoài ở trong dự án <b>Angualar</b> là như thế nào nhé.

# **1 Mô tả mục đích ví dụ**

Hôm nay chúng ta sẽ viết một ứng dụng hiển thị danh sách các nhân viên trong công ty ABC vào trong ứng dụng Angular của mình. Công ty ABC sẽ cung câp cho chúng ta một webservice. Khi gọi webservice này thì ta sẽ nhận được một đối tượng json. Trong đối tượng Json này sẽ chứa danh sách nhân viên công ty ABC. Khi đã nhận được kết quả trả về từ webservice của công ty ABC thì mình sẽ hiển kết quả đó ra cho bên view. 

Sau đây là webservice của công ty ABC : http://dummy.restapiexample.com/api/v1/employees
Nếu các em copy đường link này và gõ trên trình duyệt mình sẽ nhận được file json sau

{% highlight json linenos %}

{"status":"success","data":[{"id":"1","employee_name":"Tiger Nixon","employee_salary":"320800","employee_age":"61","profile_image":""},{"id":"2","employee_name":"Garrett Winters","employee_salary":"170750","employee_age":"63","profile_image":""},{"id":"3","employee_name":"Ashton Cox","employee_salary":"86000","employee_age":"66","profile_image":""},{"id":"4","employee_name":"Cedric Kelly","employee_salary":"433060","employee_age":"22","profile_image":""},{"id":"5","employee_name":"Airi Satou","employee_salary":"162700","employee_age":"33","profile_image":""},{"id":"6","employee_name":"Brielle Williamson","employee_salary":"372000","employee_age":"61","profile_image":""},{"id":"7","employee_name":"Herrod Chandler","employee_salary":"137500","employee_age":"59","profile_image":""},{"id":"8","employee_name":"Rhona Davidson","employee_salary":"327900","employee_age":"55","profile_image":""},{"id":"9","employee_name":"Colleen Hurst","employee_salary":"205500","employee_age":"39","profile_image":""},{"id":"10","employee_name":"Sonya Frost","employee_salary":"103600","employee_age":"23","profile_image":""},{"id":"11","employee_name":"Jena Gaines","employee_salary":"90560","employee_age":"30","profile_image":""},{"id":"12","employee_name":"Quinn Flynn","employee_salary":"342000","employee_age":"22","profile_image":""},{"id":"13","employee_name":"Charde Marshall","employee_salary":"470600","employee_age":"36","profile_image":""},{"id":"14","employee_name":"Haley Kennedy","employee_salary":"313500","employee_age":"43","profile_image":""},{"id":"15","employee_name":"Tatyana Fitzpatrick","employee_salary":"385750","employee_age":"19","profile_image":""},{"id":"16","employee_name":"Michael Silva","employee_salary":"198500","employee_age":"66","profile_image":""},{"id":"17","employee_name":"Paul Byrd","employee_salary":"725000","employee_age":"64","profile_image":""},{"id":"18","employee_name":"Gloria Little","employee_salary":"237500","employee_age":"59","profile_image":""},{"id":"19","employee_name":"Bradley Greer","employee_salary":"132000","employee_age":"41","profile_image":""},{"id":"20","employee_name":"Dai Rios","employee_salary":"217500","employee_age":"35","profile_image":""},{"id":"21","employee_name":"Jenette Caldwell","employee_salary":"345000","employee_age":"30","profile_image":""},{"id":"22","employee_name":"Yuri Berry","employee_salary":"675000","employee_age":"40","profile_image":""},{"id":"23","employee_name":"Caesar Vance","employee_salary":"106450","employee_age":"21","profile_image":""},{"id":"24","employee_name":"Doris Wilder","employee_salary":"85600","employee_age":"23","profile_image":""}]}
{% endhighlight %}

Mục đích của chúng ta là từ <b>Angular gọi webservice</b> lấy kết quả từ webservice và hiển thị dữ liệu lên trong ứng dụng Angular

<br>
# **2 Bước 1 : Khai báo thư viện HttpClient**

Để gọi được webservice ở bên ngoài thì Angular cung cấp cho chúng ta thư viện <b>HttpClient</b>, mình dùng nó để gọi các service bên ngoài. Việc đầu tiên là mình sẽ khai báo nó trong file app.module.ts như sau

{% highlight java linenos %}

import { NgModule } from '@angular/core';
import { HttpClientModule } from "@angular/common/http";

@NgModule({
  imports: [
    HttpClientModule,
    RouterModule.forRoot([
     
    ])
  ],
  bootstrap: [ AppComponent ]
})
export class AppModule { }
{% endhighlight %}

- Chúng ta import HttpClientModule từ @angular/common/http
- Trong @NgModule chúng ta import nó vào dự án imports: [ HttpClientModule]

# **3 Bước 2 : sử HttpClient gọi webservice**

Trong bài này chúng ta tạo một file tên là employee.service.ts với nội dung như sau.

{% highlight java linenos %}

import { Injectable } from "@angular/core";
import { HttpClient } from "@angular/common/http";

//To define a class as a service in Angular, use the @Injectable() decorator to provide the metadata that allows Angular
// to inject it into a component as a dependency
@Injectable({
    providedIn: "root"
})

export class EmployeeService {

    items = [];

    constructor(
        private http : HttpClient
    ){}

    addToCard(product) {
        this.items.push(product);
    }

    getItems() {
        return this.items;
    }

    clearCart() {
        this.items = [];
        return this.items;
    }
    displayAllEmployee() {
        return this.http.get('http://dummy.restapiexample.com/api/v1/employees');
    }
{% endhighlight %}

- Đầu tiên chúng ta import 2 thư viện HttpClient (dùng để gọi webservice) và Injectable (tạo ra service và mình sẽ nhúng nó vào Controller)

- Tiếp đến trong constructor chúng ta nhúng thư viện vào. Cái này gọi là <b>Dependency Injection</b>. Mình nhúng đối tượng HttpClient vào biến http. Sau đó dùng biến http để gọi các service bên ngoài. Chúng ta khai báo là  private http : HttpClient.

- Cuối cùng hàm displayEmployee ta dùng phương thức get và truyền đó là cái link webservice mà công ty ABC cung cấp cho mình.

- Trên đây là anh dùng phương thức get. Ngoài ra mình có thể dùng các phương thức khác như Post, Put , Delete

# **4 Bước 4 : Hiển thị dữ liệu lên trang web**

Ví dụ như anh sẽ tạo ra một component tên là employee. Trong component này anh sẽ có 3 files. File đầu tiên là employee.component.css dùng để trang trí cho trang web, employee.component.html dùng để hiển thị trang web cho người dùng. Và file cuối cùng là employee.component.ts . Trong file này anh sẽ nhúng service tên EmployeeService ở trên vào như sau.

{% highlight java linenos %}
import { Component, OnInit} from "@angular/core";
import { EmployeeService } from "../employee.service";


@Component({
    selector : 'app-cart',
    templateUrl : './cart.component.html',
    styleUrls : ['./cart.component.css']
})

export class EmployeeComponent {

    employees;

    constructor(
        private employeeService: EmployeeService,
        
    ) {
        this.employees = this.employeeService.displayAllEmployee();
        

    }

    onSubmit(customerData) {

        console.warn('your order has been submitted', customerData);
   
    }

}
{% endhighlight %}

- Chúng ta nhúng EmployeeService và trong Controller import { EmployeeService } from "../employee.service";
- Chúng ta Inject (nhúng) employeeService vào trong Controller thông qua constructor  private employeeService: EmployeeService
- Tiếp đến chúng ta gọi webservice : this.employeeService.displayAllEmployee(). Khi gọi xong webservice thì chúng ta sẽ nhận được đối tượng Json gồm danh sách các nhân viên. Tiếp đó ta gán kết quả này vào biến employees.
- Chúng ta sẽ truyền dữ liệu từ biến employees qua cho file  employee.component.html và hiển thị kết quả ra cho người dùng.

 **Kết luận**

 Đây chỉ là ví dụ đơn giản để các em nắm được luồng đi của một ứng dụng Angular khi gọi các webservice từ bên ngoài. Trong thực tế thì anh còn kết hợp thêm nhiều thư viện khác nữa anh hy vọng bài viết sau anh sẽ nói rõ hơn. Các em có thể xem qua một số keywork như <b>ReactRX , Obserable, subcribe , unsubcribe </b>. Và tham khảo thêm bài viết sau (đây)[https://www.learnrxjs.io/]

<br>
### Nào chúng ta hãy xem video hướng dẫn dưới đây nhé.
{% include youtubePlayer.html id=page.youtubeId %}
