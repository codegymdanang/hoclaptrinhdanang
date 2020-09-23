---
layout: course-java
title: Iterator
slug : iterator
category: laptrinhjava
tags: [java core]
summery: Iterator
image: /images/blog/java.png
featureImage: /images/post/javacore/feature_collection.png
description : Sử dụng Iterator trong lập trình java. Khái niệm Iterator trong học lập trình java. Sử dụng Iterator duyệt qua các tập hợp như List , Vector , Set , Queue, Dequee, Map.
youtubeId: 5C2OqlhiYsg
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em, hôm nay chủ đề của chúng ta sẽ hướng dẫn cách tạo ra một Iterator theo mong muốn của chúng ta.


# **1. Iterator là gì**

Thông thường chúng ta hay sử dụng vòng lặp for để duyệt qua các phần tử trong tập hợp. Hôm nay mình có thêm một công cụ mới để duyệt qua các phần tử trong tập hợp nữa đó là Iterator.

- Chúng ta sử dụng phương thức next để lấy phần tử trong tập hợp

{% highlight java linenos %}

import java.util.ArrayList;
import java.util.Iterator;

public class MyClass {
  public static void main(String[] args) {

    // Make a collection
    ArrayList<String> cars = new ArrayList<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");

    // Get the iterator
    Iterator<String> it = cars.iterator();

    // Print the first item
    System.out.println(it.next());
  }
}

{% endhighlight %}

- Duyệt qua các phần tử trong tập hợp

{% highlight java linenos %}

while(it.hasNext()) {
  System.out.println(it.next());
}

{% endhighlight %}

- Xoá một phần tử trong tập hợp

{% highlight java linenos %}

import java.util.ArrayList;
import java.util.Iterator;

public class MyClass {
  public static void main(String[] args) {
    ArrayList<Integer> numbers = new ArrayList<Integer>();
    numbers.add(12);
    numbers.add(8);
    numbers.add(2);
    numbers.add(23);
    Iterator<Integer> it = numbers.iterator();
    while(it.hasNext()) {
      Integer i = it.next();
      if(i < 10) {
        it.remove();
      }
    }
    System.out.println(numbers);
  }
}

{% endhighlight %}









