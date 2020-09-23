---
layout: course-java
title: Tính kế thừa
slug : tinh-ke-thua
category: laptrinhjava
tags: [java core]
summery: Tính kế thừa 
image: /images/blog/java.png
featureImage: /images/post/javacore/feature_oop.png
description : Hiểu về tính kế thừa trong lập trình hướng đối tượng trong lập trình? Giải thích các khái niệm về kế thừa hìnhtrong lập trình hướng đối tượng. Lợi ích của việc sử dụng lập tính đa hình.
youtubeId: MGWT_Y9Oi8I
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào bạn, nếu bạn là người mới tìm hiểu về <b>lập trình</b>, hẳn bạn đã từng nghe tới khái niệm về <b>kế thừa</b>. Nếu bạn đang không hiểu
thì bài viết sau đây sẽ giúp bạn hiểu rõ về <b>kế thừa</b> hơn các khái niệm thông qua các ví dụ thực tế. Nội dung đề cập trong bài này là


<br>
# **1. Tính kế thừa là gì**

Tính kế thừa các em hiểu nôm na giống như ngoài đời vậy. Anh lấy ví dụ như mình kế thừa ADN của cha và mẹ mình thì mình sẽ có hết tất cả các gen tốt của cha và mẹ. Trong lập trình Java khi nói đến kế thừa thì mình cũng nói khái niệm lớp cha và lớp con. Lớp con sẽ dùng từ khoá extends để mô tả nó sẽ kế thừa lớp cha. Trong lập trình khi lớp cho có 10 thuộc tính nếu lớp con kế thừa lớp cha thì mặc định lớp con có 10 thuộc tính như cha.
Anh ví dụ như mình có lớp cha là lớp Vehical (Xe cộ), trong lớp cha này mình định nghĩa các thuộc tính như color, model và phương thức run. Giả sử như anh có 1 lớp con là Bicycle hoặc Car kế thừa lớp Vihical thông qua từ khoá extends thì lúc này lớp Bicycle và Car mặc định có thuộc tính là color, model và phương thức run.

Sử dụng kế thức giúp mình tiết kiệm dòng code. Như vậy ở class Bicycle hay Car anh không phải khai báo lại biến color, model nữa.


{% highlight java linenos %}

class Vehicle {
  protected String model = "Ford"; 
  protected String color = "Red";   

  public void run() {                    
    System.out.println("Tuut, tuut!");
  }
}

class Bicycle extends Vehicle {
 
  public static void main(String[] args) {
    Bicycle myBike = Bicycle Car();
    myBike.run();
    System.out.println(myBike.color + " " + myBike.model);
  }
}

class Car extends Vehicle {

  private String modelName = "Mustang";    // Car attribute
 
  public static void main(String[] args) {
    Car myCar = new Car();
    myCar.run();
    System.out.println(myCar.color + " " + myCar.model);
  }
}


{% endhighlight %}

<br>
# **2. Không cho lớp con kế thừa**

Trong trường hợp mình có lớp cha nhưng không muốn cho lớp con kế thừa thì mình dùng từ khoá final.

{% highlight java linenos %}

final class Vehicle {
  protected String model = "Ford"; 
  protected String color = "Red";   

  public void run() {                    
    System.out.println("Tuut, tuut!");
  }
}

class Bicycle extends Vehicle {
 
  public static void main(String[] args) {
    Bicycle myBike = Bicycle Car();
    myBike.run();
    System.out.println(myBike.color + " " + myBike.model);
  }
}

{% endhighlight %}

Như vậy khi chạy chương trình thì nó sẽ báo lỗi ở lớp Bicycle vì kế thừa lớp Vehicle. Chương trình sẽ thôgn báo cho chúng ta là lớp Bicycle không thể kế thừa lớp Vehicle được 

