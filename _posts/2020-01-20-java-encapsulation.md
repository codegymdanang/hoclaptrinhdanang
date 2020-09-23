---
layout: course-java
title: Tính đóng gói
slug : tinh-dong-goi
category: laptrinhjava
tags: [java core]
summery: Tính đóng gói  
image: /images/blog/java.png
featureImage: /images/post/javacore/feature_oop.png
description : Hiểu về tính đóng gói trong lập trình hướng đối tượng trong lập trình? Giải thích các khái niệm về tính đóng gói trong lập trình hướng đối tượng. Lợi ích của việc sử dụng tính đóng gói.
youtubeId: MGWT_Y9Oi8I
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào bạn, nếu bạn là người mới tìm hiểu về <b>lập trình</b>, hẳn bạn đã từng nghe tới khái niệm về <b>tính đóng gói</b>. Nếu bạn đang không hiểu
thì bài viết sau đây sẽ giúp bạn hiểu rõ về <b>tính đóng gói</b> hơn các khái niệm thông qua các ví dụ thực tế. Nội dung đề cập trong bài này là

<br>
# **1. Tính đóng gói là gì**

Tính đóng gói đảm bảo rằng dữ liệu nhạy cảm và quan trọng sẽ bị ẩn đi từ người dung. Để làm được tính đóng gói ẩn dữ liệu quan trọng thì ta sử dụng từ khoá private cho các thuộc tính và cung cấp phương thức get và set cho các đối tượng khác muốn cập nhật giá trị hoặc lấy giá trị.

Trong ví dụ dưới đây ta muốn biến name là không được truy cập trực tiếp mà phải thông qua get và set method. Phương thức get sẽ trả về giá trị của biến name còn phương thức set sẽ gán giá trị mới cho biến name.
<br>
{% highlight java linenos %}

public class Person {
  private String name; // private = restricted access

  // Getter
  public String getName() {
    return name;
  }

  // Setter
  public void setName(String newName) {
    this.name = newName;
  }
}

{% endhighlight %}

Một khi chúng ta đã đặt biến name là private thì các lớp khác sẽ không thấy biến name trực tiếp. Nếu các lớp khác vẫn cố tình gọi thì sẽ gặp lỗi sau error: name has private access in Person
<br>
{% highlight java linenos %}

public class MyClass {
  public static void main(String[] args) {
    Person myObj = new Person();
    myObj.name = "John";  // error
    System.out.println(myObj.name); // error 
  }
}

{% endhighlight %}

# **2. Tại sao chúng ta sử dụng tính đóng gói**

- Chúng ta sẽ kiểm soát được các thuộc tính và phương thức có trong đối tượng
- Các thông tin nhạy cảm và quan trọng chỉ được phép đọc 
- Tính bảo mật cao


