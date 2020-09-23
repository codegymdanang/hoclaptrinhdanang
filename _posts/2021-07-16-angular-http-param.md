---
layout: course-angular
title: Truyền tham số cho webservice
slug : angular-call-webservice
category: laptrinhweb
tags: [angular]
summery: Truyền tham số cho webservice
image: /images/blog/angular.png
description : Hướng dẫnTruyền tham số cho webservice trong dự án Angular. Hiểu được cách truyền tham số cho webservicee trong dự án angular. Hiểu được mục đích của thư viện HTTP Client được sử dụng như thế nào để gọi các webservices.
youtubeId: edYsCowgQq0
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người cách gọi <b>Truyền tham số cho webservice</b> bên ngoài ở trong dự án <b>Angualar</b> là như thế nào nhé.

# **1. Truyền param trên URL**

Khi mình gọi webservice bên ngoài, thì có nhiều webservice yêu cầu mình thêm dữ liệu trong body để truyền lên cho webservice. Để làm được việc này ta dùng đối tượng Http Param để truyền thêm giá trị.

{% highlight javascript linenos %}

import { Injectable } from '@angular/core';
import { HttpClient, HttpParams } from '@angular/common/http';
import { Observable} from 'rxjs/Rx';
 
import { repos} from './repos';
 
@Injectable()
export class GitHubService {
 
   baseURL= "https://api.github.com/";
 
   constructor(private httpClient: HttpClient){
   }
 
   getRepos(userName: string, PageNo: string, SortOn: string): Observable<repos[]> {
 
 
        let params = new HttpParams()
                .set('page', PageNo)
                .set('sort', SortOn);
   
        console.log(params.toString());
 
        return this.httpClient.get<repos[]>(this.baseURL + 'users/' + userName + '/repos', {params});
   }
  
}

{% endhighlight %}

- Chúng ta truyền param như sau

{% highlight javascript linenos %}

this.httpClient.get<repos[]>(this.baseURL + 'users/' + userName + '/repos', {params})

{% endhighlight %}

# **2. Truyền giá trị trên http header gọi webservice**

{% highlight javascript linenos %}

getPeopleWithHeaders(): Observable<Person[]> {
    const headers = { 'content-type': 'application/json'}  
    console.log(headers)
    return this.http.get<Person[]>(this.baseURL + 'people',{'headers':headers})
  }
{% endhighlight %}

# **3. Send Cookie**

Chúng ta sử dụng tham số withCredentials=true cho request để gửi cookie

{% highlight javascript linenos %}

getReposWithCookies(userName: string): Observable<repos[]> {
 
      const params = new HttpParams()
        .set('sort', "description")
        .set('page',"2");
  
      const headers = new HttpHeaders()
        .set('Content-Type', 'application/json')
        
  
      return this.http.get<repos[]>(this.baseURL + 'users/' + userName + '/repos', { 'params': params, 'headers': headers, withCredentials: true })
        .pipe(
          map((response) => {
            return response;
          }),
          catchError((err, caught) => {
            console.error(err);
            throw err;
          }
          )
        )
    }
 

{% endhighlight %}

# **4. Bắt Errors ở Component**

{% highlight javascript linenos %}

Trong trường hợp gọi webservice sẽ xảy ra tình trạng là webservice bị lỗi. Thì chúng ta có bắt lại lỗi đó

public getRepos() {
    this.loading = true;
    this.errorMessage = "";
    this.githubService.getReposCatchError(this.userName)
      .subscribe(
        (response) => {                           //Next callback
          console.log('response received')
          this.repos = response;
        },
        (error) => {                              //Error callback
          console.error('error caught in component')
          this.errorMessage = error;
          this.loading = false;
    
          //throw error;   //You can also throw the error to a global error handler
        }
      )
  }
{% endhighlight %}

hàm subscribe cung cấp cho chúng ta 3 tham số callbacks.

{% highlight javascript linenos %}

.subscribe(success, error, completed);

{% endhighlight %}

Trong trường hợp lỗi chúng ta sẽ xử lý trong hàm error

{% highlight javascript linenos %}

(error) => {                              //Error callback
          console.error('error caught in component')
          this.errorMessage = error;
          this.loading = false;
        }

{% endhighlight %}

# **5. Bắt Errors ở Service**

Ngoài bắt lỗi ở Component chúng ta có thực hiện bắt lỗi ở Service. Chúng ta sử dụng hàm catchError.

{% highlight javascript linenos %}

getRepos(userName: string): Observable<repos[]> {
    return this.http.get<repos[]>(this.baseURL + 'usersY/' + userName + '/repos')
      .pipe(
        catchError((err) => {
          console.log('error caught in service')
          console.error(err);
 
          //Handle the error here
 
          return throwError(err);    //Rethrow it back to component
        })
      )
  }

{% endhighlight %}














