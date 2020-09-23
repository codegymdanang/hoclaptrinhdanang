---
layout: course-java
title: Java Interface
slug : interface
category: laptrinhjava
tags: [java core]
summery: Interface
image: /images/blog/java.png
featureImage: /images/post/javacore/feature_interfaces_vs_abstract.png
description : Chúng ta tìm hiểu Interface là gì? Khi nào dùng abstract, khi nào dùng Interface trong quá trình lập trình java.
youtubeId1 : hxTH18XG4qs
youtubeId2 : kfQ7O7Fky8U
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào bạn, nếu bạn là người mới tìm hiểu về lập trình, hẳn bạn đã từng nghe tới khái niệm về <b>Interface</b> trong lập trình.
Nhưng bạn có biết khi nào mình sẽ dùng interface không? 

<br>
# **1. Interface là gì**

- Như các em đã học bài học hôm trước về tính trừu tượng, nếu các em quên thì có thể xem lại tại [đây] (https://levunguyen.com/laptrinhjava/2020/01/01/tinh-truu-tuong/). Thì Interface chính là cách mà chúng ta làm tính trừu tượng trong lập trình. Ngoài cách dùng abstract class thì để thực hiện được tính trừu tượng ta có thể sử dụng Interface.

- Interface chính là 100% abstract class có nghĩa là trong abstract class ta có 10 phương thức như ta chỉ cần 5 phương thức abstract cũng được. 5 phương thức còn lại là các phương thức bình thường. Tuy nhiên nếu Abstract Class có 10 phương thức abstract thì lớp con phải Override lại 10 phương thức. Cũng tương tự như vậy tất cả các phương thức trong interface nếu có lớp con kế thừa nó thì bắt buộc lớp con phải Override lại 10 phương thức giống như abstract class vậy.

- Chúng ta sử dụng từ khoá interface để khai báo một Interface trong java.


{% highlight java linenos %}
// interface
interface Animal {
  public void animalSound(); 
  public void run(); 
}
{% endhighlight %}

- Để sử dụng được interface thì cúng ta sử dụng từ khoá implements

{% highlight java linenos %}
// Interface
interface Animal {
  public void animalSound(); // interface method (does not have a body)
  public void sleep(); // interface method (does not have a body)
}

// Pig "implements" the Animal interface
class Pig implements Animal {
  public void animalSound() {
    // The body of animalSound() is provided here
    System.out.println("The pig says: wee wee");
  }
  public void sleep() {
    // The body of sleep() is provided here
    System.out.println("Zzz");
  }
}

class MyMainClass {
  public static void main(String[] args) {
    Pig myPig = new Pig();  // Create a Pig object
    myPig.animalSound();
    myPig.sleep();
  }
}

{% endhighlight %}

- Trong Java 1 class con chỉ có thể kế thừa 1 lớp cha. Ví dụ Class Cat extends Animals mà thôi chứ không thực hiện đa kế thừa được như 
Cat extends Animals,Vihecial được

- Nhưng trong Interface chúng ta có thể thực hiện đa kế thừa được.

{% highlight java linenos %}
interface FirstInterface {
  public void myMethod(); // interface method
}

interface SecondInterface {
  public void myOtherMethod(); // interface method
}

class DemoClass implements FirstInterface, SecondInterface {
  public void myMethod() {
    System.out.println("Some text..");
  }
  public void myOtherMethod() {
    System.out.println("Some other text...");
  }
}

class MyMainClass {
  public static void main(String[] args) {
    DemoClass myObj = new DemoClass();
    myObj.myMethod();
    myObj.myOtherMethod();
  }
}
{% endhighlight %}


<br>
# **7. Demo tạo interface trong Java**  

<center>
{% include youtubePlayer.html id=page.youtubeId2 %}
</center>
