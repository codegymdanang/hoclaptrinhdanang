---
layout: course-java
title: Heap và Stack trong lập trình java
slug : bo-nho-heap-va-stack
category: laptrinhjava
tags: [java core]
summery: Bộ Nhớ Heap va Stack
image: /images/blog/java.png
featureImage: /images/post/javacore/feature_heapstack.jpeg
description : Giải thích các hoạt động của bộ nhớ heap và stack trong lập trình java. Hiểu được cách thức lưu trữ các giá trị, đối tượng trong ngôn ngữ java trong bộ nhớ heap và stack. Phân biệt được sự khác nhau giữ bộ nhớ heap và stack trong ngôn ngữ lập trình java
youtubeId: 5ix_2ALbqHY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào bạn ,chắc hẳn bạn đang phân vân khi mình khai báo biến ,object ,phương thức ,tham số thì nó sẽ được lưu ở đâu trong bộ nhớ phải không ? Ai sẽ quản lý bộ nhớ? Bài viết sau đây anh sẽ giải thích cho các bạn 2 bộ nhớ <b>Heap</b> và <b>Stack</b> lưu trữ dữ liệu gì và lưu như thế nào nhé .

<br>
# **1. Các thuật ngữ**

{:refdef: style="text-align: center;"}
![Các thuật ngữ ](/images/post/javacore/cacthuatngu.png){:class="img-responsive"}
{: refdef}

- Runtime : khoản thời gian chương trình chạy.
- Java Heap Memory : Vùng nhớ Heap trong Java.
- Java Stack Memory: Vùng nhớ Stack trong Java.
- JVM : máy ảo Java Vitural Machine để chạy các chương trình Java.
- Object : là đối tượng được khởi tạo từ khoá new từ một class. Ví dụ Persion persion = new Person().

<br>
# **2 Heap và Stack**

<b>Bộ nhớ Heap và Stack</b> là một phần của bộ nhớ được <b>JVM</b> sử dụng để chạy chương trình Java của bạn. Khi bạn chạy chương trình Java, JVM sẽ yêu cầu hệ điều hành (Ví dụ như Window,Mac, ) cấp cho một không gian bộ nhớ trong RAM để dùng cho việc chạy chương trình.
JVM sẽ chia bộ nhớ  này thành 2 vùng nhớ Heap và Stack cho việc quản lý.

{:refdef: style="text-align: center;"}
![Heap và Stack trong Java  ](/images/post/javacore/stackandheap.png){:class="img-responsive"}
{: refdef}

<br>
# **3 Bộ nhớ Heap**

- <b>Bộ nhớ Heap</b> là bộ nhớ được sử dụng ở runtime (Khi chương trình đang  chạy) để lưu các Objects(các đối   tượng) . Bất cứ khi nào ở đâu trong chương trình của bạn khi bạn tạo Object thì nó sẽ được lưu trong Heap (thực thi toán tử new).
- Các objects trong Heap đều được truy cập bởi tất cả các các nơi trong ứng dụng, bởi các threads khác nhau.
- Thời gian sống của object phụ thuộc vào chương  trình <b>Garbage Collector</b> (GC ) của java. Khi một object bị null hoặc không tham chiếu tới một đối tượng nào thì GC sẽ xoá nó khỏi bộ nhớ.
- Dung lượng sử dụng của Heap sẽ tăng giảm phụ thuộc vào Objects sử dụng.
- Dung lượng Heap thường lớn hơn Stack.

<br>
# **4 Bộ nhớ Stack**

- Bộ nhớ để lưu các biến local trong hàm.
- Các biến local bao gồm loại nguyên thuỷ (primitive) và loại tham chiếu tới đối tượng trong heap (reference) khai báo trong hàm, hoặc đối số được truyền vào hàm, thường có thời gian sống ngắn.
- Bộ  nhớ stack thường nhỏ.
- Cơ chế hoạt động thức của <b>Stack</b> là những phương thức , biến chạy sau thì sẽ bị giải phóng đầu .
- Khi hàm được gọi thì một vùng nhớ được tạo ra trong stack và lưu các biến trong hàm đó. Khi hàm thực hiện xong, khối bộ nhớ cho hàm sẽ bị xoá, và giải phóng bộ nhớ trong stack.
<br>

- Ví dụ về <b>bộ nhớ Heap</b> và <b>bộ nhớ Stack</b>

{:refdef: style="text-align: center;"}
![Ví dụ về Heap và Stack  ](/images/post/javacore/vdheapstack.png){:class="img-responsive"}
{: refdef}

{% highlight java linenos %}

public class Memory {

    public static void main (String[] args,) { // line 1
        int i = 1 ; //line 2
        Object obj = new Object(); // line 3
        Memory mem = new Memory(); // line 4
        mem.foo(obj); // line 5
    }//line 9

    private static void foo(Object param) { // line 6
        String str = param.toString(); // line 7
        System.out.println(str)// line 8
    }
}

{% endhighlight %}

- Dòng 1 phương thức public static void main sẽ lưu bên Stack (vì stack sẽ cấp phát vùng nhớ cho phương thức).
- Dòng 2 khai báo biến i = 2 thì nằm bên stack vì stack lưu các biến.
- Dòng 3 khai báo biến Object obj = new Object  thì biến obj  nằm bên stack vì stack lưu các biến còn đối tượng Object được lưu bên Heap và biến obj sẽ tham
chiếu đến đối tượng Object bên bộ nhớ Heap .
- Dòng 4 Memory mem = new Memory thì đối tượng Memory sẽ lưu bên bộ nhớ heap còn biến mem thì lưu bên bộ nhớ stack , và mem tham chiếu tới đối
tượng Memory bên Heap.
- Dòng 5  mem.foo() thì phương thức foo() được tạo ra ở dòng 5. Phương thức foo này là nằm trong phương thức main . Như ta thấy bên bộ nhớ Stack
Hình chữ nhật bự nhất bao ở ngoài là hàm main () . Bên trong hàm main là bộ nhớ phương thức foo. Khi chương trình chạy xong thì bộ nhớ foo() sẽ
được giải phóng trước sau đó mới đến main.
- Dòng 6 private void foo() thì hàm foo()  được lưu trong bộ nhó Stack.
- Dòng 7 String str = param.toString() . Trong java String là kiểu đặc biệt . Nó là kiểu Object và được quản lý bởi String Pool riêng. Chính vì vậy nó được lưu bên Heap.

<br>
# **5. Video demo Heap và Stack**

{:refdef: style="text-align: center;"}
{% include youtubePlayer.html id=page.youtubeId %}
{: refdef}
