---
layout: course-angular
title: Angular hoạt động như thế nào  
slug : angular-co-che-hoat-dong
category: laptrinhweb
tags: [angular]
summery: Cơ chế hoạt động của Angular   
image: /images/blog/angular.png
description : Angular hoạt động như thế nào. Giải thích cơ chế hoạt động của Angular
youtubeId: 977WIZTAUv8
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người cách <b>cơ chế hoạt động của Angular </b> là như thế nào?

# **1- Cấu trúc dự án Angular**

{% highlight javascript  linenos %}

├── e2e
│   ├── src
│   │   ├── app.e2e-spec.ts 
│   │   ├── app.po.ts
│   ├── protractor.conf.js 
│   ├── tsconfig.e2e.json
├── node_modules
├── src
│   ├── app
│   │   ├── app-routing.module.ts
│   │   ├── app.component.css
│   │   ├── app.component.html
│   │   ├── app.component.spec.ts
│   │   ├── app.component.ts
│   │   ├── app.module.ts
│   ├── assets
│   │   ├── .gitkeep
│   ├── environments
│   │   ├── environment.prod.ts
│   │   ├── environment.ts
│   ├── favicon.ico
│   ├── index.html
│   ├── main.ts
│   ├── polyfills.ts
│   ├── styles.css
│   ├── test.ts
├── .editorconfig
├── .gitignore
├── angular.json
│── browserslist   
├── karma.conf.js
├── package-lock.json
├── package.json
├── README.md
├── tsconfig.app.json
├── tsconfig.json
├── tsconfig.spec.json
└── tslint.json

{% endhighlight %}

- Thư mục cha (root) gồm có cá thư mục con là e2e, node_module và src. Ngoài ra có thêm một số file cấu hình bên ngoài

- File .editorcongif : file này dùng để cấu hình nếu trình soạn thảo code chúng ta dùng là Visual Studio. Mình có thể thay đổi cấu hình tại đây

- File .gitignore : dùng để nói file nào được đưa lên github file nào không được đưa lên

- angular.json : dùng để cấu hình lại Angular Cli

- browserslist : những phiên bản browser sẽ tương thích với dự án angular

- karma.config.js : file này dùng để chạy các testing (kiểm thử) các chức năng

- package.json : file này chứa các thư viện cần thiết cho dự án angular, ngoài ra nếu ta thêm một thư viện bên thứ 3 vào thì khai báo trong này

- tslint.js : dùng để kiểm tra code có chất lượng hay không, có dể đọc hay dể bảo trì không, có theo chuẩn không.

- thư mục e2e : chức các file liên quan đến việc testing. Angular sử dụng thư viên protractor để thực hiện automation test trên các trình duyệt.

- thư mục node_modules : nơi chứa các thư viện và được download về cho dự án angular. Nó được quản lý bằng NPM có nghĩa là ta dùng NPM để xoá , thêm các thư viện

- thư mục src : nơi chứa các source khi chương trình chạy. Đây là nơi tập trung các dòng code của ứng dụng angular

- thư mục app : angular cli tạo ra folder này giống như folder cha của ứng dụng. Angular cli tạo ra như một ví dụ mẫu để sau này ta tạo các component khác. Trong thư mục app thường có 

+ app.component.html : nơi chúng ta viết các files html. Là tầng view mà người dùng có thể thấy được
+ app.component.ts (component class) : là file sử lý các nghiệp vụ nó giống như Controller bên Spring Web
+ app.component.css : chúng ta định nghĩa các css mà component sẽ dùng
+ app.component.ts : file này dùng cho việc testing (kiểm thử)
+ app.module.ts        : file dùng để cấu hình cho module app
+ app-rounting.module.ts : file này dùng để điều hướng.


# **2- Cơ chế hoạt động Angular**

Angular sẽ làm các bước sau đây để hiện thị trang home khi chúng ta chạy ng serve -o

- Angular sẽ load file index.html
- Angular tiếp tục nạp các thư viện và các thư viện bên thứ 3 vào 
- Angular sẽ load file main.ts
- Trong file main.ts Angular sẽ load module cha là app.modules.ts
- Trong app.modules.ts ta load lên module cha component (root) hay còn gọi là root component. Trong dự án Angular ta sẽ có nhiều component. Mỗi component là 1 phần của view hiểu thị cho người dùng
- Trong module component sẽ có các file html,css (view) lúc đó sẽ hiển thị trang web cho người dùng

# **3- Load trang index.html đầu tiên**

File index.html là file đầu tiên mà Angular sẽ gọi khi ứng dụng được triển khai. Nội dung file index.html như sau.

{% highlight html  linenos %}
 
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>GettingStarted</title>
  <base href="/">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="icon" type="image/x-icon" href="favicon.ico">
</head>
<body>
  <app-root></app-root>
</body>
</html>

{% endhighlight %}

Như ta thấy không có file javascript và css có trong index.html. Trong thẻ body chỉ chứa 1 thẻ duy nhất là app-root.

Khi chúng ta thực hiện ng build. Angular sẽ biên dịch các file .ts các thư viện bên thứ 3 và nhúng vào index như sau. Ta có thể tìm thấy file này trong folder dist. Khi chạy lệnh ng build thì Angular sẽ tạo cho chúng ta 1 folder là dist nó nén hết tất cả file dự án lại. 

{% highlight html  linenos %}

<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>GettingStarted</title>
  <base href="/">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="icon" type="image/x-icon" href="favicon.ico">
</head>
<body>
  <app-root></app-root>
 
  <script src="runtime-es2015.js" type="module"></script>
  <script src="runtime-es5.js" nomodule defer></script>
  <script src="polyfills-es5.js" nomodule defer></script>
  <script src="polyfills-es2015.js" type="module"></script>
  <script src="styles-es2015.js" type="module"></script>
  <script src="styles-es5.js" nomodule defer></script>
  <script src="vendor-es2015.js" type="module"></script>
  <script src="vendor-es5.js" nomodule defer></script>
  <script src="main-es2015.js" type="module"></script>
  <script src="main-es5.js" nomodule defer></script></body>
</html>
{% endhighlight %}

Như vậy ta thấy angular thêm vào 5 files javascript vào trong file index.html những file này có tác dụng như sau

- runtime.js : sử dụng Webpack để triển khai chạy ứng dụng angular
- polyfills.js : hỗ trợ chạy trên nhiều trình duyệt
- styles.js  : các css
- vender.js : chứa các javascript của angular và thư viện bên thứ 3
- main.js : các code của ứng dụng mình

# **4- Application Entry Point load**

Sau khi index.html được load lên, tiếp tục các thư viện Angular, thư viện bên thứ 3 được load. Angular cần tìm file đầu tiên để load ứng dụng file này được gọi là Application Entry Point

Trong Angular thì file đó là main.ts. Chúng ta có thể tìm thấy nó ở dưới folder src. Khi file này được load lên nó sẽ load tất cả các components mà ta khai báo trong dự án

Để kiểm tra entry là file nào. Chúng ta vào file angular.json. Trong thẻ architect có chứa thẻ main chúng ta khai báo entry point là src/main.ts

{% highlight javascript  linenos %}

{
  "$schema": "./node_modules/@angular/cli/lib/config/schema.json",
  "version": 1,
  "newProjectRoot": "projects",
  "projects": {
    "GettingStarted": {
      "projectType": "application",
      "schematics": {},
      "root": "",
      "sourceRoot": "src",
      "prefix": "app",
      "architect": {
        "build": {
          "builder": "@angular-devkit/build-angular:browser",
          "options": {
            "outputPath": "dist/GettingStarted",
            "index": "src/index.html",
            "main": "src/main.ts",                        <====
            "polyfills": "src/polyfills.ts",
            "tsConfig": "tsconfig.app.json",
            "aot": false,
            "assets": [
              "src/favicon.ico",
              "src/assets"
            ],
            "styles": [
              "src/styles.css"
            ],
            "scripts": []
          },
      }
    }
 }
{% endhighlight %}

# **5- Chức năng main.ts**

File main.ts có nội dung như sau.

{% highlight javascript  linenos %}

import { enableProdMode } from '@angular/core';
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';
 
import { AppModule } from './app/app.module';
import { environment } from './environments/environment';
 
if (environment.production) {
  enableProdMode();
}
 
platformBrowserDynamic().bootstrapModule(AppModule)
  .catch(err => console.error(err));
{% endhighlight %}

- Chúng ta thấy mình import platformBrowserDynamic để nói Angular là mình sẽ load ứng dụng Angular bằng trình duyệt trên desktop. Angualr có nhiều cách để load ứng dụng có thể trên mobile hoặc các ứng dụng hybrid.

- Tiếp đến chugns ta thấy Angular import AppModule. AppModule là component cha của cả ứng dụng Angualr. Angular tổ chức code theo modules. Module cha có nhiều module con, module con có nhiều module cháu cứ như vậy mà kéo dài. Như vậy AppModule là module cha của ứng dụng Angular. Tât cả các ứng dụng angular phải có ít nhất 1 module cha để load lên đầu tiên ta gọi nó là root module. Sau dó đến các module con

# **5- Root Module**

Như vậy angular sẽ load file AppModule đầu tiên. File AppModule mô tả sau đây.

{% highlight javascript  linenos %}

import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
 
import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
 
@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
{% endhighlight %}

- Sau khi root module được gọi lên thì nó cần tối thiều 1 component được load lên. Trong ví dụ này ta sẽ load component đầu tiền là AppComponent. Trong dự án Angular ta sẽ có 1 component cha, trong component cha sẽ có nhiều component con. Đưới đây là khai báo component được load lên

{% highlight javascript  linenos %}

import { AppComponent } from './app.component';

{% endhighlight %}

Chúng ta sử dụng annotation @NgModule để khai báo các module con và các thirdparties sẽ được dùng trong ứng dụng

{% highlight javascript  linenos %}

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }

{% endhighlight %}

- imports : chúng ta dùng để nhúng các modules bên ngoài các thirdparties sẽ được dùng chung với ứng dung angular

- declarations : chúng ta khai báo các components như cha, con các directive hoặc service mà ta sử dụng trong dự án angular.

- boostrap : chỉ ra component nào Angualr sẽ load lên khi Angular Module được load

# **6- Component**

Trong Root Module chỗ boostrap : [AppComponent] ta nói cho Angular biết là phải load AppComponent lên. Thì Code Component được hiện thi như sau

{% highlight javascript  linenos %}

import { Component } from '@angular/core';
 
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'GettingStarted';
}
 
{% endhighlight %}

- Để tạo được 1 component cần cho ít nhất 3 files. 1 đó là file Class Component mà ta thấy ở trên. 2 là file html hiển thị view, 3 là file css để trang trí

- Class Component được đánh dâú với annotation là @Component trong đó có 3 thuộc tính selector, templateURL và styleUrls. Trong đó

- selector dùng để chỉ ra nơi nào sẽ được nhúng component này vào web. Chúng ta thấy selector tên là app-root. Nếu nhìn vào file index.html ta cũng thấy thẻ app-root.

{% highlight javascript  linenos %}

<body>
  <app-root></app-root>
</body>
{% endhighlight %}

Như vậy thẻ app-root này sẽ chứ dựng giao diện của html của App Component. Trong html thông thường thì không có thẻ <app-root> thẻ này do chính chúng ta định nghĩa ra.

- templateUrl : nơi đặt file html ở đâu

- styleUrls : nơi đặt css ở đâu 

Như vậy khi chạy ng -server -o ta sẽ thấy được giao diện HTML được định nghĩa trong templateURL là file app.component.html



















