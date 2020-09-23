---
layout: course-java
title: Tham trị và tham chiếu trong lập trình java
slug : tham-tri-va-tham-chieu
category: laptrinhjava
tags: [java core]
summery: Pass by value
image: /images/blog/java.png
featureImage: /images/post/javacore/feature_passbyvalue.png
description : Tham trị pass by value và tham chiếu pass by reference là 2 cách thức hoạt động khác nhau. Trong bài viết sau sẽ giải thích cách thức hoạt động của tham trị và tham chiếu. Cùng tìm hiểu tham trị là gì, tham chiếu là gì trong bài viết sau đâu nhé.
youtubeId: 0F_8a5_fKno
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn, chắc chắn không ý bạn nhầm lẫn khái niệm <b>tham trị</b> và <b>tham chiếu</b>  ? Có rất nhiều bạn có nhận định chưa đúng về khái niệm
Ví dụ như các bạn nói các tham số trong hàm nếu ta truyền kiểu nguyên thuỷ thì đó là <b>tham trị</b> còn nếu truyền kiểu object là <b>tham chiếu</b>.
Hôm nay anh sẽ giải thích cho các bạn hiểu rõ 2 khái niệm này nhé. Để hiểu được bài viết này thì các em nên đọc qua bài viết về (bộ nhớ)[https://levunguyen.com/laptrinhjava/2020/04/07/phan-biet-bo-nho-heap-va-stack/] để nắm được cách lưu trữ các giá trị trong lập trình

<br>
# **1. Gán giá trị**

Trước hết mình xem lại  bộ nhớ máy tính lưu trữ các biến và giá trị mình như thế nào?. Nếu các bạn còn chưa rõ về cách lưu trữ thì có thể xem lại bài viết bộ nhớ tại (đây)[https://levunguyen.com/laptrinhjava/2020/04/07/phan-biet-bo-nho-heap-va-stack/]

- Bộ nhớ chương trình gồm có 2 thành phần chính là địa chỉ bộ nhớ và dữ liệu được lưu trữ trong bộ nhớ đó
- Ví dụ khi mình gán một biến cho một giá trị như test = 3. Như vậy bộ nhớ cần lưu trữ chữ test và giá trị 3 của nó vào bộ nhớ như sau

{:class="table table-bordered"}
 |  Địa chỉ bộ nhớ   	| 	Giá trị ô nhớ                     |   
 |---	                |---	                        |
 |   xx1 	            |     test                          |
 |   xx2 	            |         3                      |

<br>
# **2.Tham trị là gì  (pass by value)**

<b>Tham trị</b> <b>Pass by value</b> : nghĩa là mình sẽ clone (tạo ra một giá trị mới bằng cách copy giá trị gốc), và mình chỉ thao táo giá trị với bản copy.
Khi chúng ta thay đổi các giá trị của đối tượng, thì không ảnh hưởng đến giá trị gốc. Pass-by-value được hiểu là khi bạn thay đổi biến trong hàm thì ngoài hàm sẽ không bị ảnh hưởng.


{:refdef: style="text-align: center;"}
![Tham trị](/images/post/javacore/passbyvalue.png){:class="img-responsive"}
{: refdef}

- Ở ví dụ trên ta thấy rất rõ giá trị của biến  someValue
- Ở hàm main chúng ta khai báo nó là giá trị 7 . Sau đó ta gọi hàm process(int value) và truyền giá trị 7 vào.
- Mặc dù ta gián lại giá trị someValue = 10 . Nhưng khi kết thúc hàm process thì giá trị someValue là bằng 7 chứ không phải là 10.
- Bởi vì chúng ta chỉ thao tác với giá trị copy chứ không phải giá trị gốc , nên ta gán someVaule = 10 là gián cho giá trị copy = 10.
- Như vậy dù trong hàm process(int value ) ta có thay đổi giá trị như thế nào đi chăng nữa thì lúc thoát ra khỏi hàm process(int value) giá trị
gốc vẫn không thay đổi .

{:refdef: style="text-align: center;"}
![Tham trị](/images/post/javacore/passbyvalue2.png){:class="img-responsive"}
{: refdef}

Sau khi hàm process(int value) thực hiện xong nhiệm vụ của mình , thì sẽ bị giải phóng đi , trả lại bộ nhớ cho chương trình , giá trị clone
(copy) cũng được giải phóng trả lại bộ nhớ.

<br>
# **3. Truyền tham  chiếu**

<b>Tham chiếu</b> Pass by reference. Ngược lại với Pass by value, giá trị gốc sẽ bị thay đổi <b>Pass-by-reference</b> là khi bạn thay đổi biến trong hàm cũng làm ngoài hàm bị ảnh hưởng.
Nó giống như bạn truyền đúng địa chỉ của biến đó vào hàm.

{:refdef: style="text-align: center;"}
![Tham trị](/images/post/javacore/passbyreference.png){:class="img-responsive"}
{: refdef}

Trong trường hợp này hàm process(int &value) trỏ thằng tới địa chỉ vùng nhớ nơi lưu giá trị 7. Như vậy khi ta thay đổi giá trị trong hàm nó thay
đổi luôn giá trị khác .

<br>
# **4. Tổng kết**

Các bạn nên nhớ trong  Java là 100% truyền tham trị (passed by value). Mình chỉ clone một giá trị từ giá trị gốc sau đó truyền đi
cho các method cần dùng nó. Ta chỉ thay đổi giá trị Clone chứ không thay đổi trực tiếp giá trị  vùng nhớ của đối tượng gốc
