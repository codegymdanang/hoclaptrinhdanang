---
layout: course-html
title: Giới thiệu  
slug : html-gioi-thieu
category: laptrinhweb
tags: [html]
summery: HTML là gì   
image: /images/blog/angular.png
description : Sử dụng HTML trong dự án làm web. Hướng dẫn sử dụng HTML vào dự án web. 
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người cách sử dụng <b>HTML</b> là như thế nào?

# **1. HTML là gì**

Vào những thập niên 80 khi con người muốn chia sẽ tài liệu với nhau thì mình thường copy tài liệu như word hay excel vào usb sau đưa cho người khác mở lên. Cách này rất bất tiện vì mọi người không thể chia sẽ dữ liệu với nhau được. HTML ra đời giúp cho tài liệu được chia sẽ trực tuyến trên mạng. Nó giúp cho tài liệu của chúng ta được hiển thị một cách bắt mắt và có tổ chức, các tài liệu có thể link trực tiếp qua lại với nhau được. Cụ thể như các em thấy ngày nay HTML được dùng để định dạng ra các trang web, hiển thị nội dung một cách trực quan và rất tiện lợi.

# **2. Cú pháp khai báo thẻ HTML**

HTML dùng để format lại dữ liệu hiển thị trên website. HTML cung cấp cho chúng ta những cú pháp chuẩn mà khi tuân thủ các cú pháp đó thì dữ liệu sẽ được hiển thị như chúng ta mong muốn. Cú pháp để khai báo một thẻ HTML như sau.

{% highlight html linenos %}

<Tên thẻ > Nội dung </ Đóng tên thẻ>

{% endhighlight %} 

- Ví dụ như ta muốn hiển thị một dòng chữ trên tài liệu. Thì trong HTML chúng ta sử dụng thẻ h1 như sau

{% highlight html linenos %}

<h1>This is a heading</h1>

{% endhighlight %} 

Như vậy ta có thẻ mở HTML là \< h1 \> và thẻ đóng html là \< \/h1 \>

# **3. Các thẻ HTML cơ bản**

- Ví dụ ta có một file HTML như sau

{% highlight html linenos %}

<!DOCTYPE html>
<html>

   <head>
      <title>This is document title</title>
   </head>
	
   <body>
      <h1>This is a heading</h1>
      <p>Document content goes here.....</p>
   </body>
	
</html>


{% endhighlight %} 

- !Doctype html : Dòng này dùng để khai báo phiên bản HTML mà ta sử dụng. Khi khai báo như trên chúng ta thông báo là đang dùng phiên bản mới nhất là 5. Khi sử dụng phiên bản mới nhất của HTML thì chúng ta có thêm nhiều chức năng mới của HTML. HTML có rất nhiều phiên bản từ 1.0, 2.x, 3.x , 4.x và phiên bản mới nhất là 5.

- hmlt 	: Thẻ này dùng để khai báo bắt đầu một trang HTML. Nó bao gồm các thẻ head và body của tài liệu HTML

- head 	: Sử dụng để ghi các thông tin về tài liệu HTML nó bao gồm các thể title và meta

- title : Thẻ này dùng để đặt tên cho website

- body 	: Hiển thị nội dung trang web bên trong thẻ body. Thẻ body chứa đựng nội dung của website

- h1 	:  Hiển thị phần mở đầu của một tài liệu hoặc một đoạn văn bản.

- p 	:  Dùng để hiển thị một đoạn văn bản.

Như vậy ta thấy một trang HTML cơ bản phải có những phần trên. Tuỳ vào mỗi loại văn bản hiển thị mà chúng ta sẽ viết thêm code trong phần body với các thẻ mà HTML cung cấp cho mình.

# **4. Thẻ title**

Thẻ title dùng để đặt tên cho website. Ví dụ như blog của anh mọi người sẽ thấy cái tab trên trình duyệt là học lập trình

- Ví dụ ta có một file HTML như sau

{% highlight html linenos %}

<!DOCTYPE html>
<html>

   <head>
      <title>Học lập trình</title>
   </head>

   <body>
      <p>Hello, World!</p>
   </body>

</html>


{% endhighlight %} 

{:refdef: style="text-align: center;"}
![title1](/images/post/html/title1.png){:class="img-responsive"}
{: refdef}


# **5. Thẻ base**

Thẻ base được sử dụng với mục đích tất cả các trang đường link trong website sẽ được nối thêm vào bởi url được khai báo trong thẻ base. Ví dụ ta có thể base là https://levunguyen.com và ta có trang about. Thì nó sẽ được nối lại là https://levunguyen.com/about.

{% highlight html linenos %}

<!DOCTYPE html>
<html>

   <head>
      <title>HTML Base Tag Example</title>
      <base href = "https://www.tutorialspoint.com/" />
   </head>

   <body>
      <img src = "/images/logo.png" alt = "Logo Image"/>
      <a href = "/html/index.htm" title = "HTML Tutorial"/>HTML Tutorial</a> 
   </body>

</html>


{% endhighlight %} 


- Kết quả ở trên ta sẽ có đường link là https://levunguyen.com/images/logo.png và https://levunguyen.com/html/index.htm


# **5. Thẻ link**

Thẻ link dùng để liên kết tài liệu HTML với những tài liệu bên ngoài hoặc các file liên quan bên ngoài. Trong ví dụ này ta sử dụng HTML liên kết với Css (CSS là công cụ để ta trang trí website đẹp hơn).

{% highlight html linenos %}

<!DOCTYPE html>
<html>

   <head>
      <title>HTML link Tag Example</title>
      <base href = "https://www.tutorialspoint.com/" />
      <link rel = "stylesheet" type = "text/css" href = "/css/style.css">
   </head>
	
   <body>
      <p>Hello, World!</p>
   </body>
	
</html>


{% endhighlight %} 

# **5. Thẻ Style**

Chúng ta sử dụng thẻ style để trang trí cho website. Chúng ta có thể thay đổi, thêm màu sắc và website thông qua thẻ style.


{% highlight html linenos %}

<!DOCTYPE html>
<html>

   <head>
      <title>HTML style Tag Example</title>
      <base href = "https://www.tutorialspoint.com/" />
      
      <style type = "text/css">
         .myclass {
            background-color: #aaa;
            padding: 10px;
         }
      </style>
   </head>
	
   <body>
      <p class = "myclass">Hello, World!</p>
   </body>

</html>


{% endhighlight %} 

- Trong thẻ style chúng ta khai báo một class là .myclass. Trong class này ta nhóm các thuộc tính như màu sắc , padding.

- Để sử dụng được myclass trong style thì trong thẻ p ta sử dụng thuộc tính class và giá trị là tên myclass mà ta định nghĩa trong style. Kết quả thẻ p sẽ có background là màu xám và padding 10px.


Trong các bài tiếp theo anh sẽ giới thiệu thêm các thẻ HTML để xây dựng nên một website.




