---
layout: course-java
title: Cài đặt HashSet
slug : hashset
category: laptrinhjava
tags: [java core]
summery: HashSet
image: /images/blog/java.png
featureImage: /images/post/javacore/feature_collection.png
description : HashSet là gì? Các phương thức có trong HashSet và cách sử dụng HashSet
youtubeId: 5C2OqlhiYsg
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em, hôm nay chủ đề của chúng ta sẽ hướng dẫn cách tạo ra một HashSet theo mong muốn của chúng ta.

# **1. HashSet là gì**

HashSet là một trong những tập hợp để lưu trữ các phần tử trong bộ java collection. HashSet lưu các phần tử không trùng lặp nhau và là duy nhất. Anh ví dụ như lưu số chứng mình nhân dân của tất cả các học sinh trong lớp A012920. Nhưng vậy mỗi học sinh là có một số chứng minh nhân dân duy nhất và không bị trùng nhau.

- Tạo HashSet


{% highlight java linenos %}

import java.util.HashSet; // Import the HashSet class

HashSet<String> cars = new HashSet<String>();

{% endhighlight %}

- Thêm một phần tử chúng ta dùng phương thức add

{% highlight java linenos %}

public class MyClass {
  public static void main(String[] args) {
    HashSet<String> cars = new HashSet<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("BMW");
    cars.add("Mazda");
    System.out.println(cars);
  }
}

{% endhighlight %}

- Kiểm tra phần tử đó có tồn tại hay chưa ta dùng phương thức contains

{% highlight java linenos %}

cars.contains("Mazda");

{% endhighlight %}

- Xoá một phần tử dùng phương thức remove

{% highlight java linenos %}

cars.remove("Volvo");

{% endhighlight %}

- Xoá hết các phần tử dùng phương thức clear

{% highlight java linenos %}

cars.clear();

{% endhighlight %}

- Lấy kích thướt của tập hợp dùng phương thức size

{% highlight java linenos %}

cars.size();

{% endhighlight %}

- Duyệt qua các phần tử dùng vòng lặp for

{% highlight java linenos %}

for (String i : cars) {
  System.out.println(i);
}

{% endhighlight %}




