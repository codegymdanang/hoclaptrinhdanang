---
layout: course-java
title: Khai Báo Biến
slug : bien
category: laptrinhjava
tags: [java core]
summery: Biến  
image: /images/blog/java.png

description : Hiểu về Biến là gì trong lập trình hướng đối tượng trong lập trình? Giải thích các khái niệm về Biến trong lập trình hướng đối tượng. Lợi ích của việc sử dụng biến lập trình hướng đối tượng trong lập trình.
youtubeId: fR05ShUphxA
---

# **Giới thiệu nội dung bài viết**

Chào các em. Hôm nay chủ đề của chúng ta sẽ về Biến trong lập trình java.

{% include toc.html %}

<br>
# **1. Biến là gì**

Trong lập trình chúng ta sử dụng biến để lưu lại giá trị để thao tác. Anh lấy ví dụ mình muốn phát triển chương trình quản lý sinh viên thì các giá trị của sinh viên như tên, tuổi, địa chỉ và mã số sinh viên thì mình cần có một cái để lưu lại cho chương trình sử lý. Cái mà lưu lại các giá trị đó gọi là biến.

# **2. Các loại biến**

Trong lập trình Java ta có các loại biến sau.

- String  : dùng để lưu các giá trị chuỗi ví dụ như tên sinh viên là Nguyễn Văn A
- int     : dùng để lưu các giá trị số ví dụ như số điện thoại 0903049583
- float   : dùng để lưu các giá trị số thập phân như tiền tệ 1.000.500 VND
- char    : dùng để lưu 1 ký tự ví dụ ký tự a hoặc b
- boolean : dùng để lưu giá trị đúng hay sai.

 # **3. Khai báo biến**

Chúng ta khai báo biến với cú pháp như sau

{% highlight java  %}

type variable = value;

{% endhighlight %}

- type     : là loại biến có thể là String, int , float, char hoặc boolean
- variable : là tên của biến
- value    : giá trị của biến

Ví dụ ta tạo một biến tên là name và chứa giá trị là "Le Vu Nguyen"

{% highlight java  %}

String name = "Le Vu Nguyen";

{% endhighlight %}

Hoặc trong trường hợp này anh tạo một biến có tên là phoneNumber và gán giá trị là 15 cho nó. 

{% highlight java  %}

int phoneNumber = 15;

{% endhighlight %}

Chú ý nếu chúng ta giá gán giá trị mới cho giá trị cũ thì nó sẽ ghi đè lên giá trị cũ. Ví dụ lúc đầu anh gán giá trị num=15 nhưng sau đó anh đổi thành num=20 thì giá trị cuối cùng của num là 20

{% highlight java  %}

int num = 15;
num = 20;  // myNum is now 20
System.out.println(myNum);

{% endhighlight %}

Biến được gán với từ khoá final thì giá trị sẽ không được thay đổi và gán giá trị mới. Trong ví dụ bên dưới anh tạo biến num với từ khoá final và gán giá trị là 15. Nếu anh gán lại giá trị 20 thì sẽ xảy ra lỗi, vì final là từ khoá mình dùng khai báo khi muốn giá trị đó là không thể thay đổi.

{% highlight java  %}

final int num = 15;
num = 20;

{% endhighlight %}

 # **4. Hiển thị giá trị trong biến**

 Để hiển thị giá trị trong biến ta sử dụng hàm println()

{% highlight java  %}

String name = "John";
System.out.println("Hello " + name);

{% endhighlight %}

Chúng ta có thể dùng dấu + để kết hợp 2 biến lại với nhau và in ra kết quả

{% highlight java  %}

String firstName = "Le ";
String lastName = "Vu Nguyen";
String fullName = firstName + lastName;
System.out.println(fullName);

{% endhighlight %}

Chúng ta có thể khai báo nhiều biến trên cùng 1 dòng. Nhưng trong thực tế lập trình anh ít khi làm vậy vì không đẹp code

{% highlight java  %}

int x = 5, y = 6, z = 50;
System.out.println(x + y + z);

{% endhighlight %}





