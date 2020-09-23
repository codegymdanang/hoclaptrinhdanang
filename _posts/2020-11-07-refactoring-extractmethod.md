---
layout: blog
title: Kỷ thuật Extract Method
slug:  extract-method
category: craftmanship
tags: [refactoring]
summery: Kỷ thuật Extract Method
image: /images/blog/design-patterns.png
description : kỷ thuật Extract Method là gì, hướng dẫn extract method , ví dụ extract method
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các e, chủ đề hôm nay của anh sẽ bàn về kỷ thuật <b>Extract Method</b> ? Kỷ thuật nằm nhằm làm cho một method dài khó đọc
trở thành một phương thức nhỏ hơn , dể đọc hơn.

<br>
# Vấn đề đang gặp  ?
Như ví dụ mình có đoạn code sau đây.
<br>
{% highlight java linenos %}
void printOwing() {
  printBanner();

  // Print details.
  System.out.println("name: " + name);
  System.out.println("amount: " + getOutstanding());
}
{% endhighlight %}

Như vậy , các em sẽ thấy đoạn code ở trên có vấn đề ở chổ . Trong hàm printOwing đầu tiên là mình in printBanner(),
sau đó mình lại tiếp tục viết các dòng code để in chi tiết (Print details) . Như vậy không hợp lý lắm mà thay vào đó mình
nên nhóm các dòng code in chi tiết (Print details) thành một method để mình gọi thôi.  

<br>
# Giải quyết vấn đề bằng kỷ thuật Extract Method

{% highlight java linenos %}
void printOwing() {
  printBanner();
  printDetails(getOutstanding());
}

void printDetails(double outstanding) {
  System.out.println("name: " + name);
  System.out.println("amount: " + outstanding);
}
{% endhighlight %}

Như các em có thể thấy cách giải quyết ở trên , mình tạo một method mới tên là printDetails() sau đó mình dời hết tất
cả các dòng code liên quan đến print detail lại với nhau và để nó trong method printDetails(). Tiếp đến ta chỉ cần gọi nó
trong method printOwing() là xong.  

<br>
# Tổng kết

Như các em có thể thấy phương pháp Extract Method giúp mình nhóm các dòng code liên qua lại với nhau thành một method, Các method dài quá 30 dòng
thì các em nên tách thành những method nhỏ hơn. Trong lập trình mỗi method tối đa 15 -> 20 dòng là chuẩn.

Mỗi method chỉ nên làm duy nhất một nhiệm vụ . Anh ví dụ như printDetails thì nhiệm vụ của nó chỉ in chi tiết thôi chứ không làm các công việc khác
trong method printDetails
