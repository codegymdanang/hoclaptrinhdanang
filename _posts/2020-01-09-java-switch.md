---
layout: course-java
title: Mệnh đề Switch
slug : switch
category: laptrinhjava
tags: [java core]
summery: Switch  
image: /images/blog/java.png

description : Hiểu về Switch là gì trong lập trình hướng đối tượng trong lập trình? Giải thích các khái niệm về Switch trong lập trình hướng đối tượng. Lợi ích của việc sử dụng Switch lập trình hướng đối tượng trong lập trình.
youtubeId: fR05ShUphxA
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em. Hôm nay chủ đề của chúng ta sẽ về Switch trong lập trình java. Switch dùng để chọn thực thi một khối lệnh đúng trong nhiều khối lệnh đưa ra.

- If : kiểm tra nếu đều kiện đúng, ta thực hiện các câu lệnh trong khối lệnh if.
- Else : kiểm tra điều kiện và  thực hiện các khối lệnh ngược lại với điều kiện
- Else If : tạo thêm một điều kiện mới nếu điều kiện trước đó là false
- Switch  : gồm nhiều điều kiện if và else

# **2. Cú pháp Switch**

{% highlight java  %}

switch(expression) {
  case x:
    // code block
    break;
  case y:
    // code block
    break;
  default:
    // code block
}

{% endhighlight %}

- switch : sẽ kiểm tra giá trị expression
- case   : nếu giá trị trong expression mà đúng với case thì sẽ chạy khối lệnh trong case
- break  : dùng để thoát ra khỏi switch
- default : khi không có giá trị nào thoả mãn thì sẽ chạy khối lệnh trong default

- Trong ví dụ dưới đây ta kiểm tra xem hôm nay là thứ mấy. Trong mệnh đề switch ta có 7 trường hợp xảy ra từ thứ 2 đến thứ 7. Tuỳ vào giá trị truyền vào là số nào thì sẽ vào case tương ứng. Như ví dụ dưới đây ta truyền vào day = 4 thì nó sẽ rơi vào case 4 và in ra là thứ 5

{% highlight java  %}

int day = 4;
switch (day) {
  case 1:
    System.out.println("Monday");
    break;
  case 2:
    System.out.println("Tuesday");
    break;
  case 3:
    System.out.println("Wednesday");
    break;
  case 4:
    System.out.println("Thursday");
    break;
  case 5:
    System.out.println("Friday");
    break;
  case 6:
    System.out.println("Saturday");
    break;
  case 7:
    System.out.println("Sunday");
    break;
}
//Kết quả là "Thursday" (day 4)
{% endhighlight %}


















