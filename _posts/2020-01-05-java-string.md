---
layout: course-java
title: Java String
slug : string
category: laptrinhjava
tags: [java core]
summery: Strings  
image: /images/blog/java.png

description : Hiểu về Strings là gì trong lập trình hướng đối tượng trong lập trình? Giải thích các khái niệm về Strings trong lập trình hướng đối tượng. Lợi ích của việc sử dụng Stringss lập trình hướng đối tượng trong lập trình.
youtubeId: fR05ShUphxA
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em. Hôm nay chủ đề của chúng ta sẽ về Strings trong lập trình java.


<br>
# **1. Strings là gì**

String được sử dụng để lưu trữ các giá trị Text (gồm nhiều ký tự). Ví dụ nhưng 

{% highlight java  %}

String greeting = "Hello";

{% endhighlight %}

String là một kiểu dữ liệu đặt biệt, nó thật ra là một đối tượng chứa đựng nhiều phương thức để xử lý một số nhiệm vụ như sau.

# **2. String length**

- Dùng để lấy độ dài của một chuỗi

{% highlight java  %}

String txt = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
System.out.println("The length of the txt string is: " + txt.length());

{% endhighlight %}


# **3. String toUperCase và toLowerCase**

- Dùng để chuyển hoá chữ thành chữ hoa và chữ thường

{% highlight java  %}

String txt = "Hello World";
System.out.println(txt.toUpperCase());   // Outputs "HELLO WORLD"
System.out.println(txt.toLowerCase());   // Outputs "hello world"

{% endhighlight %}

# **4. String IndexOf**

- Dùng để trả về vị trí 1 ký tự trong chuỗi

{% highlight java  %}

String txt = "Please locate where 'locate' occurs!";
System.out.println(txt.indexOf("locate")); // Outputs 7

{% endhighlight %}

# **5. String Concatenation**

- Dùng để nối 2 chuỗi lại với nhau

{% highlight java  %}

String firstName = "John";
String lastName = "Doe";
System.out.println(firstName + " " + lastName);

{% endhighlight %}

# **5. String hiển thị các giá trị đặt biệt**

- Dùng để hiển thị các ký tự như đấu 1 nháy, 2 nháy. Ví dụ khi ta biến sau 

{% highlight java  %}

String text = " le vu" nguyen"

{% endhighlight %}

- Như vậy thì sẽ bị lỗi vì dấu 2 nháy sau chữ vu sẽ gây nhầm lẫn cho trình biên dịch. Như vậy làm sao sử dụng được chữ vu". Thì ta dùng ký tự \ đằng trước đấu 2 nháy như sau.

{% highlight java  %}

String txt = "le vu\" nguyen";

{% endhighlight %}

Ngoài ra String hỗ trợ các ký tự đặt biệt khác như

- \n : dùng để xuống dòng.

{% highlight java  %}

String txt = "Hello\nWorld!";

{% endhighlight %}


- \t : cách nhau một khoảng tab

{% highlight java  %}

 String txt = "Hello\tWorld!";

{% endhighlight %}
- \b : cách nhau một khoảng backspace

{% highlight java  %}

String txt = "Hello\tWorld!";

{% endhighlight %}


# **5. Dấu +**

Khi ta sử dụng dấu + thì đối với kiểu int thì nó là cộng 2 số, còn đối với kiểu String thì sẽ là concatenation (nối chuỗi)

{% highlight java  %}

int x = 10;
int y = 20;
int z = x + y;      // z là 30

{% endhighlight %}

{% highlight java  %}

String x = "10";
String y = "20";
String z = x + y;   // z là chuỗi 1020 

{% endhighlight %}


