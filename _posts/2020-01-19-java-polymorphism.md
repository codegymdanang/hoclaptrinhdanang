---
layout: course-java
title: Tính đa hình
slug : tinh-da-hinh
category: laptrinhjava
tags: [java core]
summery: Tính đa hình  
image: /images/blog/java.png
featureImage: /images/post/javacore/feature_oop.png
description : Hiểu về tính đa hình trong lập trình hướng đối tượng trong lập trình? Giải thích các khái niệm về tính đa hìnhtrong lập trình hướng đối tượng. Lợi ích của việc sử dụng lập tính đa hình.
youtubeId: MGWT_Y9Oi8I
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào bạn, nếu bạn là người mới tìm hiểu về <b>lập trình</b>, hẳn bạn đã từng nghe tới khái niệm về <b>tính đa hình</b>. Nếu bạn đang không hiểu
thì bài viết sau đây sẽ giúp bạn hiểu rõ về <b>tính đa hình</b> hơn các khái niệm thông qua các ví dụ thực tế.

<br>
# **1. Tính đa hình là gì**

Tính đa hình có nghĩa là cùng một hành động nhưng ở những ngữ cảnh khác nhau thì cho ra những hành động khác nhau, hoặc cho ra các kết quả khác nhau.

Anh lấy ví dụ như mình có lớp cha là Animal (động vật), trong lớp Animal thì mình sẽ có phương thức là makeSound() (tiếng kêu của động vật). Giả sử mình có 4 lớp con là Pig (lợn), Cat (mèo), Dog (chó), Bird (chim). Tất cả chúng đều là động vật cả nên chúng sẽ kế thừa các phương thức makeSound và các thuộc tính của lớp cha Animal. Nhưng ở phương thức makeSound ở mỗi loài động vật khác nhau. Ví dụ như con Pig kết quả của hàm makeSound sẽ cho ra tiếng kêu ủn ỉn, con Cat thì hàm makeSound là meo meo, con chó thì hàm makeSound là gâu gâu. Như vậy chúng ta thấy tính đa hình ở chỗ. Cũng là phương thức makeSound nhưng trong ngữ cảnh là con Mèo thì ta sẽ viết code riêng để xử lý tiếng kêu con mèo và trả về kết quả là tiếng kêu con mèo. Còn nếu ngữ cảnh là con Dog thì ta viết code xử lý cho con chó và trả về tiếng kêu con chó.

Trong lập trình cũng vậy mình sử dụng tính đa hình để có thể giúp mình viết ít code lại và dòng code mình sẽ dể dàng mở rộng sau này.

{% highlight java linenos %}
class Animal {
  public void makeSound() {
    System.out.println("Động vật kêu");
  }
}

class Pig extends Animal {
  public void makeSound() {
    System.out.println("The pig says: ủn ỉn");
  }
}

class Dog extends Animal {
  public void makeSound() {
    System.out.println("The dog says: gâu gâu");
  }
}


class MyMainClass {
  public static void main(String[] args) {
    Animal myAnimal = new Animal();  
    Animal myPig = new Pig();  
    Animal myDog = new Dog();  
    myAnimal.makeSound(); //lúc này sẽ in ra là ("Động vật kêu")
    myPig.makeSound(); // lúc này sẽ in ra là ("The pig says: ủn ỉn");
    myDog.makeSound();// luc này sẽ in là là ("The dog says: gâu gâu")
  }

{% endhighlight %}

<br>
# **2. Tổng kết**

Như vậy chúng ta thấy đa hình ở chỗ myAnimal.makeSound(); myPig.makeSound() ; myDog.makeSound(). Cũng là một phương thức makeSound() như nếu là con chó thì kết quả khác, con heo là kết quả khác
