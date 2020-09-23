---
layout: course-goodcode
title: Giới thiệu về Mockito
slug : mockito-la-gi
category: unitest
tags: [mockito]
summery: Mockito    
image: /images/blog/quality-code.png
description : Sử dụng mockito trong dự án java. Hướng dẫn cài đặt mockito vào dự án java. 
youtubeId: LdLvwsj5_Sk
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn, chắc hẳn bạn sẽ muốn biết <b>Mockito</b> là gì ? Trong bài viết hôm nay a sẽ giới thiệu từng bước giúp chúng ta có thể lập trình với Mockito một cách hiệu quả nhất.

<br>
# **1. Unit Testing là gì**

Unit test là một trong những kỷ thuật của testing (kiểm thử phần mềm), mục đích để kiểm tra xem từng chức năng của ứng dụng có chạy đúng yêu cầu hay không? Unit test được viết trong quá trình phát triển phần mềm và được hầu hết các lập trình viên sử dụng để đảm bảo chất lượng code mình viết ra chạy đúng theo yêu cầu của khách hàng và xảy ra ít bugs. Unit test có nghĩa là mình test một chức năng độc lập. Anh lấy ví dụ như mình có class là Person trong Person có 3 hành động là đi, nhảy, chạy như sau

<br>

{% highlight java linenos %}

public class Person {

  public void run(String[] args) {
    // cài đặt chức năng chạy    
  }

  public void jump(String[] args) {
    // cài đặt chức năng nhảy    
  }

  public void walk(String[] args) {
    // cài đặt chức năng đi bộ    
  }
}

{% endhighlight %}

Unit Test thì mình chỉ áp dụng test cho một hàm (phương thức) tại một thời điểm. Như vậy Class Persion có 3 hàm (3 đơn vị test). Chúng ta sẽ viết 3 Unit test khác nhau tương ứng cho 3 hàm. 

Unit Test có nghĩa là test một đơn vị nhỏ nhất trong Class, mà trong class đơn vị nhỏ nhất chính là phương thức. Trong thực tế một class thường có nhiều phương thức, ứng với mỗi phương thức sẽ có ít nhất 1 unitest để test cho phương thức đó. Trong các dự án mà anh từng làm thì yêu cầu Unit Test cho tất cả các method có trong Class để đảm bảo code viết ra đúng yêu cầu và giảm thiểu bugs thất nhất có thể.

<br>
# **2. Mock là gì**

Mock chính là kỷ thuật mà lập trình viên dùng để tạo ra những đối tượng (object) giả. Anh lấy ví dụ có chức năng login. Luồng đi chính sẽ từ giao diện gọi xuống controller từ controller sẽ gọi service và từ service gọi xuống Dao để insert vào database. 

Controller sẽ do developer A viết, Service do developer B viết, và Dao do developer C viết. Như vậy các em thấy khi chức năng login muốn hoàn thành thì developer A phải chờ developer B viết xong thì developer A mới test được. Tương tự như vậy developer B phải chờ developer C viết xong chức năng thao tác database thì developer B mới test được. Như vậy chúng ta sẽ mất thời gian rất lâu vì phải chờ nhau. 

Kỷ thuật mock ra đời giúp developer A có thể giả lập Service của Developer B để thực hiện việc kiểm tra xem code mình viết chạy có đúng không. Như vậy developer A vẫn tiếp tục viết code của mình và sử dụng Mock giả để viết tiếp code test của mình trong khi đó developer B vẫn đang hoàn thiện Service của mình. 

Sau khi developer B viết xong thì developer sẽ xoá mock giả đi và gắn Service thật của B viết vào. Vậy là developer A không cần chờ developer phải hoàn thành 100% công việc mới tiếp công việc của mình.

Trong khi làm Unitest các anh hay sử dụng Mock để giả lập các service được sẽ được test. Mặc dù có thể chức năng đó chưa làm xong hoặc đang làm.

<br>
# **4. Mockito là gì**

Mockito là một framework được sử dụng trong Unit Test cho các ứng dụng về Java. Nó cung cấp cho chúng ta những thư viện như mock (tạo các đối tượng giả), chạy các unitest, giả lập các tham số và phương thức. Sử dụng nó rất tiện cho việc làm Unit Test. Trong Java chúng ta có thể kết hợp Mockito với Junit hoặc TestNG để viết các test cho các phương thức trong class của mình.

Trong các bài sau chúng ta sẽ học cách sử dụng Mockito để thực hiện các unit test cho từng method của mình.  











