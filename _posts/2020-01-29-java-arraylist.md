---
layout: course-java
title: ArrayList
slug : arraylist
category: laptrinhjava
tags: [java core]
summery: ArrayList
image: /images/blog/java.png
featureImage: /images/post/javacore/feature_collection.png
description : Array List là gì? Các phương thức có trong ArrayList và cách sử dụng ArrayList
youtubeId: SkajVxpYq7k
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em, hôm nay chủ đề của chúng ta về ArrayList. Khi nào thì mình sẽ sử dụng nó nhé

<br>
# **1. ArrayList là gì**

ArrayList là một trong những tập hợp trong bộ Java Collection. ArrayList có thể linh động co giản kích thướt tuỳ ý không như Array[] kích thước khai báo cố định. Trong ArrayList các phần tử có thể được thêm,xoá một cách linh động.

- Để sử tạo được ArrayList chúng ta sẽ import gói thư viện java util vào

{% highlight java linenos %}
import java.util.ArrayList; // import the ArrayList class

ArrayList<String> cars = new ArrayList<String>(); // Create an ArrayList object
{% endhighlight %}

- Để thêm 1 phần tử chúng ta dùng phương thức add

{% highlight java linenos %}

public class MyClass {
  public static void main(String[] args) {
    ArrayList<String> cars = new ArrayList<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");
    System.out.println(cars);
  }
}
{% endhighlight %}

- Để lấy một phần tử chúng ta dùng phương thức get và truyền vào vị trí ta muốn lấy

{% highlight java linenos %}

cars.get(0);

{% endhighlight %}

- Để thay đổi giá trị trong phần tử chúng ta dùng phương thức set

{% highlight java linenos %}

cars.set(0, "Opel");

{% endhighlight %}

- Để xoá một phần tử chúng ta dùng phương thức removee và truyền vào vị trí cần xoá

{% highlight java linenos %}

cars.remove(0);

{% endhighlight %}

- Để xoá tất cả các phần tử trong tập hợp ta dùng phương thức clear

{% highlight java linenos %}

cars.clear();

{% endhighlight %}

- Để lấy tổng số phần tử trong tập hợp ta dùng phương thức size

{% highlight java linenos %}

cars.size();

{% endhighlight %}

- Để duyệt các phần tử trong mảng chúng ta dùng vòng lặp

{% highlight java linenos %}

public class MyClass {
  public static void main(String[] args) {
    ArrayList<String> cars = new ArrayList<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");
    for (int i = 0; i < cars.size(); i++) {
      System.out.println(cars.get(i));
    }
  }
}

{% endhighlight %}


- Ngoài ra chúng ta còn có thể sử dụng for each

{% highlight java linenos %}
public class MyClass {
  public static void main(String[] args) {
    ArrayList<String> cars = new ArrayList<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");
    for (String i : cars) {
      System.out.println(i);
    }
  }
}

{% endhighlight %}













