---
layout: course-java
title: Kiểu dữ liệu
slug : kieu-du-lieu
category: laptrinhjava
tags: [java core]
summery: Kiểu dữ liệu  
image: /images/blog/java.png

description : Hiểu về  Kiểu dữ liệu là gì trong lập trình hướng đối tượng trong lập trình? Giải thích các khái niệm về  Kiểu dữ liệu trong lập trình hướng đối tượng. Lợi ích của việc sử dụng  Kiểu dữ liệu trong lập trình hướng đối tượng trong lập trình.
youtubeId: fR05ShUphxA
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em. Hôm nay chủ đề của chúng ta sẽ về  Kiểu dữ liệu trong lập trình java.

<br>
# **Kiểu dữ liệu là gì**

Trong lập trình Java chúng ta có 2 loại kiểu dữ liệu đó là kiểu nguyên thuỷ và kiểu đối tượng.

# **1.  Kiểu dữ liệu Nguyên Thuỷ**

- Kiểu nguyên thuỷ bao gồm có các loại sau. Ứng với mỗi loại kiểu dữ liệu bộ nhớ sẽ cấp phát vùng nhớ tương ứng

{:class="table table-bordered"}
|  kiểu dữ liệu		  	 	|  kích thướt		            |   khoảng giá trị	|
|---	                 	|---	                        |---	     	    |
| byte			         	|	1 byte						| từ -128 đến 127	|
| short						|	2 bytes						| từ -32.768 đến 32.676	|	
| int 						|	4 bytes						| từ -2.147.483.648 đến 2.147.483.647	|
| long						|	8 bytes						| từ -9.223.372.036.854.775.808 to 9.223.372.036.854.775.807 |
| float						|	4 bytes						| 6 đến 7 thập phân 1.000,1232321 |
| double					|	8 bytes						| 15 dấu thập phân |
| boolean					|	1 bit						| chứa giá trị true hoặc false|
| char						|	2 bytes						| chứa các ký tự đơn |


# **2.  Kiểu dữ liệu Integer**

- Byte có thể chứa giá trị từ -128 đến 127. 

{% highlight java  %}

byte myNum = 100;
System.out.println(myNum);

{% endhighlight %}

- Short có thể chứa giá trị từ -32768 to 32767

{% highlight java  %}

short myNum = 5000;
System.out.println(myNum);

{% endhighlight %}

- int chứa giá trị từ  -2147483648 to 2147483647

{% highlight java  %}

int myNum = 100000;
System.out.println(myNum);

{% endhighlight %}

- long chứa giá trị từ -9223372036854775808 to 9223372036854775807

{% highlight java  %}

long myNum = 15000000000L;
System.out.println(myNum);

{% endhighlight %}

# **3.  Kiểu dữ liệu Float**

- float chứa từ 3.4e−038 to 3.4e+038

{% highlight java  %}

float myNum = 5.75f;
System.out.println(myNum);

{% endhighlight %}

- double chứa giá trị từ 1.7e−308 to 1.7e+308

{% highlight java  %}

double myNum = 19.99d;
System.out.println(myNum);

{% endhighlight %}


# **4.  Kiểu dữ liệu Khoa học**

Chúng ta có thể dùng e để mô tả  bội số của 10.

{% highlight java  %}

float f1 = 35e3f;
double d1 = 12E4d;
System.out.println(f1);
System.out.println(d1);

{% endhighlight %}

# **4.  Kiểu dữ liệu Boolean**

- Chỉ chứa kết quả đúng hay sai

{% highlight java  %}

boolean isJavaFun = true;
boolean isFishTasty = false;
System.out.println(isJavaFun);     
System.out.println(isFishTasty); 

{% endhighlight %}

# **5.  Kiểu dữ liệu ký tự**

- Kiểu char chỉ chứa 1 ký tự duy nhất

{% highlight java  %}

char myGrade = 'B';
System.out.println(myGrade);

{% endhighlight %}

- Trong kiểu ký tự chúng ta có thể sử dụng bảng mã ASCII để hiển thị giá trị


{% highlight java  %}

char a = 65, b = 66, c = 67;
System.out.println(a);
System.out.println(b);
System.out.println(c);

{% endhighlight %}

# **5.  Kiểu dữ liệu chuỗi**

- Kiểu String dùng để lưu dạng chuỗi các ký tự

{% highlight java  %}

String greeting = "Hello World";
System.out.println(greeting);

{% endhighlight %}

# **5.  Kiểu dữ đối tượng**

- Kiểu dữ liệu đối tượng thường tham chiếu tới 1 đối tượng. Anh lấy ví dụ như 

{% highlight java  %}

Student student = new Student()

{% endhighlight %}



