---
layout: course-java
title: Cài đặt HashMap
slug : hashmap
category: laptrinhjava
tags: [java core]
summery: HashMap
image: /images/blog/java.png
featureImage: /images/post/javacore/feature_collection.png
description : HashMap là gì? Các phương thức có trong HashMap và cách sử dụng HashMap
youtubeId: 5C2OqlhiYsg
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em, hôm nay chủ đề của chúng ta sẽ hướng dẫn cách tạo ra một HashMap theo mong muốn của chúng ta.

# **1. HashMap là gì**

HashMap là một trong những tập hợp để lưu trữ các phần tử. Nó khác với cách lưu của ArrayList ở chỗ nó lưu theo dạng key và value. Anh ví dụ sinh viên thường có mã sinh viên và thông tin sinh viên. Như vậy key ở đây chính là mã sinh viên còn thông tin sinh viên chính là giá trị. Dựa vào key mà chúng ta có thể lấy ra sinh viên tương ứng. Key là giá trị duy nhất không trung lặp. Như các em thấy mã sinh viên thì là duy nhất không có bạn nào trùng.

- Tạo một Hashmap

{% highlight java linenos %}

import java.util.HashMap; // import the HashMap class

HashMap<String, String> capitalCities = new HashMap<String, String>();

{% endhighlight %}

- Thêm một phần tử vào HashMap

{% highlight java linenos %}

public class MyClass {
  public static void main(String[] args) {
    // Create a HashMap object called capitalCities
    HashMap<String, String> capitalCities = new HashMap<String, String>();

    // Add keys and values (Country, City)
    capitalCities.put("England", "London");
    capitalCities.put("Germany", "Berlin");
    capitalCities.put("Norway", "Oslo");
    capitalCities.put("USA", "Washington DC");
    System.out.println(capitalCities);
  }
}

{% endhighlight %}

- Lấy một phần tử trong HashMap ta dùng phương thức get

{% highlight java linenos %}

capitalCities.get("England");

{% endhighlight %}

- Xoá một phần tử ta dùng phương thức remove

{% highlight java linenos %}

capitalCities.remove("England");

{% endhighlight %}

- Xoá hết các phần tử ta dùng phương thức clear

{% highlight java linenos %}

capitalCities.clear();

{% endhighlight %}

- Lấy kích thướt của tập hợp ta dùng phương thức size

{% highlight java linenos %}

capitalCities.size();

{% endhighlight %}

- Duyệt qua các phần tử ta dùng vòng lặp for

{% highlight java linenos %}

for (String i : capitalCities.keySet()) {
  System.out.println(i);
}

{% endhighlight %}








