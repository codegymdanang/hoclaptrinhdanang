---
layout: course-angular
title: Tạo dự án bằng angular cli  
slug : angular-tao-du-an
category: laptrinhweb
tags: [angular]
summery: Tạo dự án   
image: /images/blog/angular.png
description : Sử dụng angular cli tạo dự án angular. Hướng dẫn angular cli tạo dự án Angular. Hướng dẫn các tạo một ứng dụng angular cli.
youtubeId: 977WIZTAUv8
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người cách <b>sử dụng Angular Cli để tạo  dự án Angular</b> là như thế nào?


# **1- Angular Cli là gì**

Chúng ta sử dụng tool Angular Cli để giúp chúng ta tạo dự án một cách nhanh chóng. Nó tự động cấu hình các file và package của dự án angular cho chúng ta một cách tự động. Ngoài ra chúng ta sử dụng Angular Cli để tạo các components, directive hay service vào trong dự án có sẳn chỉ bằng 1 dòng lệnh.


# **2- Cài đặt Angular Cli**

- Bước 1 : Chúngt a cài Angular Cli bằng cách sử dụng lệnh npm install như sau. Lúc này nó sẽ lấy phiên bản mới nhất của Angular Cli

{% highlight javascript  linenos %}

npm install -g @angular/cli@latest

{% endhighlight %}

Chúng ta có thể kiểm tra phiên bản angular cli bằng lệnh --version như sau. Phiên bản anh đang dùng là 9.0.1

{% highlight javascript  linenos %}

ng --version

{% endhighlight %}

- Bước 2 : Tạo dự án angular bằng lệnh ng new

{% highlight javascript  linenos %}

ng new HotelProject

{% endhighlight %}

Câu lệnh ở trên sẽ tự động tạo ra folder dự án Angular, lấy các thư viện angular và các thư viện phụ thuộc khác của dự án. Cài đặt và cấu hình typescript (ngôn ngữ dùng để lập trình angular), cuối cùng là cài đặt các thư viện liên quan đến việc testing cho dự án angular.

- Bước 3 : Chạy dự án angular bằng lệnh ng serve

{% highlight javascript  linenos %}

ng serve 

{% endhighlight %}

Khi chạy lệnh ng server sẽ biên dịch dự án angular và Webpack server để triển khai code Angular lên server. WebPack chạy với port 4200. Sau khi code Angular được biên dịch xong. Ta có thể kiểm tra bằng cách vào browser và gõ http://localhost:4000. Ta sẽ nhận được trang home của Angular như sau.


{:refdef: style="text-align: center;"}
![angular](/images/post/angular/angular-home.png){:class="img-responsive"}
{: refdef}

Ngoài ra chúng ta có thể nói angular biên dịch và mở trình duyệt lên tự động bằng câu lệnh

{% highlight javascript  linenos %}

ng serve -o

{% endhighlight %}

# **3- Cấu trúc dự án Angular**

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































