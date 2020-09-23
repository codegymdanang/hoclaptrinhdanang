---
layout: course-angular
title: Angular Http Client  
slug : angular-dependency-injection
category: laptrinhweb
tags: [angular]
summery: Http Client   
image: /images/blog/angular.png
description : Sử dụng Http Client trong dự án angular. Hướng dẫn cài đặt Http Client vào dự án Angular.
youtubeId: dđ
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>Http Client</b> là như thế nào?

# **1. Http Client là gì**

Chúng ta sử dụng Http Client để gọi các service bên ngoài. Ví dụ như ứng dụng angular gọi các webservice của Spring. Hoặc chúng ta sử dụng các webservice của bên thứ 3. Chúng ta sử dụng thư viện HTTP Client để gọi các webservice này

Để sử dụng được HTTP Client ta làm các bước sau

Bước 1.  khai báo HttpClientModule trong app.module 

{% highlight javascript linenos %}

import { NgModule } from '@angular/core';
import { HttpClientModule } from '@angular/common/http';
 
@NgModule({
    declarations: [
        AppComponent
    ],
    imports: [
        HttpClientModule
    ],
    providers: [],
    bootstrap: [AppComponent]
})
export class AppModule { }

{% endhighlight %} 

Bước 2 : Inject HttpClient vào Service nơi sẽ gọi các webservice bên ngoài thông qua constructor

{% highlight javascript linenos %}

constructor(public http: HttpClient) {
}
{% endhighlight %} 

Bước 3 : Thực hiện các phương thức gọi ra bên ngoài. Chúng ta có thể gọi phương thức protocol là get, push, delete , update. Thông qua phương thức HttpClient.get 

{% highlight javascript linenos %}

public getData() {
  this.HttpClient.get<any[]>(this.baseUrl+'users/'+this.userName+'/repos')
           .subscribe(data => {
               this.repos= data;
           },
           error => {
           }
  );
}
{% endhighlight %}

# **2. Sử dụng Observable**

Chúng ta sử dụng Obserable trong angular để quản lý các dữ liệu bất đồng bộ. Anh ví dụ như mình gọi một webservice ở bên ngoài, sau khi kết thúc thì nó trả về đối tượng Obserable cho mình.

Obserable quản lý các đối tượng subscribes, khi có một sự thay đổi thì Obserable sẽ thông báo đến các subscribers của mình. 

Trong angular chúng ta sử dụng Obserable từ thư viện RxJS. Thư viện này cung cấp cho chúng ta một số phương thức như map , filter, take, merge kết quả của webservice gọi về.

Anh sẽ có ví dụ sau, chức năng của anh sẽ hiển thị thông tin của company ra cho người dùng. Từ Angular anh sẽ gọi ra một webservice bên ngoài. Sau khi nhận được kết quả anh sẽ hiển thị lên cho người dùng. 3 từ khoá quan trọng là Obserable , Subscribe và RxJS sẽ được sử dụng trong ví dụ này.

Bước 1 : Anh sẽ sử dụng HTTP Client để gọi ra webservice bên ngoài. Anh sẽ có file InfoCompanyService sau.

{% highlight javascript linenos %}

import { Injectable } from '@angular/core';
import { HttpClient, HttpParams } from '@angular/common/http';
import { Observable } from 'rxjs';
import { map } from 'rxjs/operators';
import { Company } from '../../models/company';

@Injectable()
export class InfoCompanyService {

  constructor(  private http: HttpClient,) {
  }
  getInfoCompany(slug): Observable<Company> {
    return this.http.get('http://localhost:8080/companies/1')
    .pipe(
      map((response: any) => response),
    )
  }
  
}
{% endhighlight %}

Đầu tiên chúng ta import thư viện Obserable

{% highlight javascript linenos %}

import { Observable } from 'rxjs';

{% endhighlight %}

Tiếp đến chúng ta gọi webservice bên ngoài tại phương thức getInfoCompany. Phương thức này sau khi gọi xong sẽ trả về kết qủa là đối tượng Obserable

{% highlight javascript linenos %}

 getInfoCompany(slug): Observable<Company> {
    return this.http.get('http://localhost:8080/companies/1')
    .pipe(
      map((response: any) => response),
    )
  }
{% endhighlight %}

Chúng ta gọi webservice bên ngoài bằng câu lệnh 

{% highlight javascript linenos %}

this.http.get('http://localhost:8080/companies/')

{% endhighlight %}

Chúng ta sử dụng hàm pipe (giống như Promise) để nhận biết khi nào dữ liệu bị thay đổi, trong trường hợp này chúng ta gọi webservice nó sẽ trả cho ta dữ liệu như vậy các đoạn code trong hàm pipe thực thi khi ta gọi xong webservice, có nghĩa là webservice trả về kết quả lúc đó ta mới chạy tiếp hàm map.

Trong hàm map chúng ta chỉ format lại dữ liệu và trả về kết quả của webservice trả về 

Bước 2 : Gọi Service từ component

Chúng ta sẽ viết component tên là Company. Trong Component này chúng ta sẽ nhúng CompanyService vào và gọi hàm getInfoCompany

{% highlight javascript linenos %}

import { Component, OnInit } from '@angular/core';
import { InfoCompanyService } from '../../../core/services/company/InfoCompany.service'
import { Company } from '../../../core/models/company';
@Component({
  selector: 'companies',
  templateUrl: './companies.component.html',
  styleUrls: ['./companies.component.scss']
})
export class ListCompanyComponent implements OnInit {

  company:Company;

  constructor(
    private infoCompanyService : InfoCompanyService
  ) {
  }

  ngOnInit() {
    this.getIdcompany();
  }
  getInfoCompany (){
    this.infoCompanyService.getInfoAllCompany().subscribe(company => this.company = company);
    
  } 
}

{% endhighlight %}


Chúng ta nhúng InfoCompanyService vào component và gọi hàm getInfoAllCompany. Lúc này InfoCompanyService sẽ gọi ra ngoài và lấy kết quả về là một Obserable. Như ta nói ở phía trên Obserable quản lý các đối tượng subscribes, khi có một sự thay đổi thì Obserable sẽ thông báo đến các subscribers của mình.  Chính vì vậy mà chúng ta phải có phương thức subscribe để nhận kết quả trả về từ Obserable

{% highlight javascript linenos %}

this.infoCompanyService.getInfoAllCompany().subscribe(companies => this.companies = companies);

{% endhighlight %}

Sau khi nhận được kết quả từ Obserable chúng ta gán biến local   this.companies = companies sau đó ta truyền biến này qua cho template html


{% highlight javascript linenos %}

<div class="container-fluid company-container header_area">
    <div class="title-box">
        <h2 class="title-center">{{'company.mainTitleListCompany' | translate}}</h2>
        <p class="description text-center">{{'company.smallTitleListCompany' | translate}}</p>
    </div>
    <div class="row">
        <div class="items-grid">
            <div class="col-xs-12 col-sm-6 col-md-4 col-lg-2" *ngFor="let company of companies">
                <company-item [company]="company"></company-item>
            </div>
        </div>
    </div>
</div>

{% endhighlight %}












