---
layout: course-java
title: Java Abstract
slug : abstract
category: laptrinhjava
tags: [java core]
summery: Abstract
image: /images/blog/java.png
featureImage: /images/post/javacore/feature_interfaces_vs_abstract.png
description : Chúng ta tìm hiểu Abstract là gì? Khi nào dùng abstract, khi nào dùng Abstract trong quá trình lập trình java.
youtubeId1 : hxTH18XG4qs
youtubeId2 : kfQ7O7Fky8U
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào bạn, nếu bạn là người mới tìm hiểu về lập trình, hẳn bạn đã từng nghe tới khái niệm về <b>Abstract</b> trong lập trình.
Nhưng bạn có biết khi nào mình sẽ dùng Abstract không? 

<br>
# **1. Abstract là gì**

Trừa tượng có nghĩa là tuyến trình che giấu đi những chi tiết quan trọng và chỉ hiển thị những thông tin cần thiết cho người sử dụng. Để thực hiện được tính trừu tượng chúng ta sử dụng từ khoá abstract hoặc interface. Trong bài này anh sẽ giới thiệu về các sử dụng abstract. Chúng ta có thể áp dụng từ khoá abstract cho class hoặc method. Khi áp dụng abstract cho class thì chúng ta không thể tạo đối tượng từ lớp abstract được. Abstract method chỉ được sử dụng và khai báo trong abstract class. Abstract method sẽ không có phần thân (code thực thi). Phần thân code thực thi sẽ được viết bởi lớp con kế thừa abstract class.

- Abstract class Animal ví dụ sau đây dùng từ khoá abstract. Chú ý chúng ta không thể tạo đối tượng Animal ani = new Animal() được.

<br>
{% highlight java linenos %}

abstract class Animal {
  public abstract void animalSound();
  public void sleep() {
    System.out.println("Zzz");
  }
}

{% endhighlight %}

- Ví dụ hoàn chỉnh về abstract class và code thực thi abstract method trong lớp con
<br>
{% highlight java linenos %}

// Abstract class
abstract class Animal {
  // Abstract method (does not have a body)
  public abstract void animalSound();
  // Regular method
  public void sleep() {
    System.out.println("Zzz");
  }
}

// Subclass (inherit from Animal)
class Pig extends Animal {
  public void animalSound() {
    // The body of animalSound() is provided here
    System.out.println("The pig says: wee wee");
  }
}

class MyMainClass {
  public static void main(String[] args) {
    Pig myPig = new Pig(); // Create a Pig object
    myPig.animalSound();
    myPig.sleep();
  }
}

{% endhighlight %}

# **2. Tại sao chúng ta sử dụng Abstract**

- Để đảm bảo tính bảo mật.
- Chúng ta chỉ đưa ra những thông tin cần thiết và che giấu những thông tin quan trọng



