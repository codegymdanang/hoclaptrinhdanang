---
layout: course-java
title: Sự khác  giữa abstract và interface trong học lập trình
slug : su-khac-nhau-giua-abstract-interface
category: laptrinhjava
tags: [java core]
summery: Abstract và Interface
image: /images/blog/java.png
featureImage: /images/post/javacore/feature_interfaces_vs_abstract.png
description : Chúng ta tìm hiểu Interface là gì ? Abstract là gì? Phân biệt sự khác giữa abstract và interface trong lập trình java. Khi nào dùng abstract, khi nào dùng interface trong quá trình lập trình java.
youtubeId1 : hxTH18XG4qs
youtubeId2 : kfQ7O7Fky8U
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào bạn, nếu bạn là người mới tìm hiểu về lập trình, hẳn bạn đã từng nghe tới khái niệm về <b>Abstract</b> và <b>Interface</b>.
Nhưng bạn có biết khi nào mình sẽ dùng abstract và khi nào mình dùng interface không? Khi mới bước chân vào
nghề lập trình anh cũng rất hoang mang về công dụng và lợi ý của Abstract và Interface. Chính vì vậy anh
viết bài này nhằm giúp mọi người có cái nhìn rõ hơn sự <b>khác nhau giữa abstract và interface</b>. Bài viết hôm nay sẽ xoay quanh các chủ đề sau.

<br>
# **1. Interface là gì**

<b>Interface</b> chính là cách mình áp dụng <b>tính trừu tượng</b> trong lập trình. Interface chính là 100% abstract class (khi tạo một lớp abstract ta có thể có 5 phương thức là abstract còn lại 5 phương thức không cần abstract. Như vậy khi lớp con kế thừa thì bắt buộc cài đặt 5 phương thức còn 5 phương thức kia không cần cài đặt. Nếu một lớp abstract có 10 phương thức abstract thì bắt buộc lớp con phải cài đặt 10 phương thức, như vậy là cũng giống interface khi ta có 10 phương thức thì lớp con cũng phải cài đặt 10 phương thức. Nói các khác interface chính là abstract class nếu lớp abstract class đó tất cả các method đều là abstract method) để nhóm các phương thức liên quan với nhau và không có
phần thân. Phần thân của method sẽ được implement (cài đặt) ở trong lớp implement Interface.

{% highlight java linenos %}
// Interface
interface Animal {
  public void animalSound(); // method của Interface không có phần thân
  public void sleep(); //method của Interface không có phần thân
}

// Pig "implements"  Interface  Animal
class Pig implements Animal {
  public void animalSound() {
    // phần thân của interface sẽ được code  trong class PI
    System.out.println("The pig says: wee wee");
  }
  public void sleep() {
    // phần thân của interface sẽ được code trong class PIG
    System.out.println("Zzz");
  }
}

{% endhighlight %}

Một số chú ý khi sử dụng Interface.

- Cũng giống như Abstract Class. Chúng ta không thể tạo đối tượng từ Interface bằng toán tử new
- Interface thì chứa method trống không có phần thân. Phần thân sẽ được code bởi những class implement (cài đặt) interface đó
- Lớp cài đặt Interface phải implement hết tất cả các method có trong interface. Nó định nghĩa một mẫu chung các hành động mà các lớp implements nó follow theo.
- Các method trong Interface mặc định là abstract  public và
- Các biến (thuộc tính) trong Interface mặc định là public,static và final  
- Các lớp có thể cài đặt (implements) một hoặc nhiều Interface.
- Interface thì không có constructor chính vì vậy mà ta không thể tạo object của một Interface được

<br>
# **2. Abstract là gì**

<b>Data Abstraction</b> là quá trình che giấu đi những dữ liệu quan trọng mình chỉ đưa ra những thông tin cần thiết cho người dùng. Để làm được abstraction trong lập  ta
có thể sử dụng abstract và interface . Ta có thể sử dụng abstract cho class hoặc method .Chúng ta sử dụng từ khoá abstract để khai báo abstract class và method.

- <b>Abstract class</b> : cũng giống như Interface chúng ta không thể tạo đối tượng từ Abstract Class
- <b>Abstract method</b> : cũng giống như Interface chúng không có phần thân . Phần thân sẽ được cài đặt trong lớp kế thừa nó

{% highlight java linenos %}

// Abstract class
abstract class Animal {
  // abstract class không có phần
  public abstract void animalSound();

  // abstract class không có phần thân
  public void sleep() {
    System.out.println("Zzz");
  }
}


class Pig extends Animal {
  public void animalSound() {
    // phần code thực thi của abstract method được viết bới lớp con kế thừa nó
    System.out.println("The pig says: wee wee");
  }
}

{% endhighlight %}

<br>
# **3. Sự khác nhau giữa abstract và interface**

Bảng dưới đây sẽ giúp các em có cái nhìn rõ hơn về <b>sự khác nhau giữa abstract và interface</b>. Khi nào thì chúng ta nên sử dụng abstract hoặc interface cho hợp lý

 {:class="table table-bordered"}
 |  Các điểm so sánh  	|  Abstract	                    |   Interface	                                  |
 |---	                |---	                        |---	     	                                  |
 |   Đa kế thừa 	    | Không hỗ trợ đa kế thừa	    | Một class có thể kế thừa nhiều Interface        |
 |   Defaul (mặc định) 	| Có thể định nghĩa thuộc tính , và thân phương thức có thể chứa code 	    | chỉ chứa hằng số , không có code trong phần thân method |
 |   Access Modifier	                |   có thể đặt tất cả modifier	    |   Mọi phương thức và thuộc tính là  public	        |  
 |   Mục đích sử dụng                   |     IS  A (quan hệ cha con)    |    HAS A (Can do, có khả năng làm được việc gì)    |

<br>
# **4. Khi nào dùng abstract**

- Khả năng mở rộng không cần xoá hết code làm lại.
- Tăng tính bảo mật che dấu các dữ liệu quan trọng
- Khi các lớp có mối liên hệ cha con  với nhau ví dụ như con gà , chó , mèo  chúng đều là động vật (Animal)

<br>
# **5. Khi nào dùng interface**

- Mục đích chính của interface là dùng cho tính đa hình. Khả năng thực hiện các hành động khác nhau trên các ngữ cảnh khác nhau.
- Chúng ta muốn các lớp không liên quan với nhau liên kết lại với nhau. Anh ví dụ như mình có phương thức thanh toán HSBC , mình có  thanh toán Vietcombank . 2 Class này hoàn toàn không liên quan gì với nhau. Ví dụ như trong ứng dụng của anh. Anh mong muốn hỗ trợ người dùng cả 2 phương thức thanh toán, có nghĩa là nếu họ có tài khoản bên HSBC họ có thể thực hiện giao dịch thanh toán , chuyển khoản bên Vietcombank. Để làm được việc đó thì 2 class HSBC và Vietcombank phải nói chuyện được với nhau, có nghỉa là 2 class đó phải có cùng một điểm chung. Thì lúc này anh sẽ tạo ra một Interface là Payment . Sau đó HSBC và Vietcombank cùng implements nó. Như vậy 2 cái đó sẽ có một điểm chung nên có thể nói chuyện được với nhau.
- Chúng ta muốn chú trọng vào hành động hơn  về cấu trúc đối tượng.
- Chúng ta muốn sử dụng đa thừa kế.
- Tăng cường tính bảo mật . Người dùng chỉ có thể thấy được method nhưng không thấy được nội dung code bên trong

<br>
# **6. Cách tạo abstract trong Java**  

<center>
{% include youtubePlayer.html id=page.youtubeId1 %}
</center>

<br>
# **7. Demo tạo interface trong Java**  

<center>
{% include youtubePlayer.html id=page.youtubeId2 %}
</center>
