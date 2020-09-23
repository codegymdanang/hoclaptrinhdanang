---
layout: course-design-pattern
title: Design Pattern trong lập trình ?
slug: design-pattern
category: craftmanship
tags: [designpattern]
summery: Design Pattern là gì
image: /images/blog/design-patterns.png
description : Hiểu design pattern là gì ? vì sao sử dụng design pattern. Hướng dẫn các mẫu design pattern trong học lập trình java.
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**
Chào các e, chủ đề hôm nay của anh sẽ bàn về chủ đề  <b>Design Pattern</b>

<br>
# Design Pattern là gì ?

<b>Design Pattern</b> là một giải pháp cho một vấn đề chung trong thiết kế phần mềm . Nó mô tả cách giải quyết một vấn đề được lập đi lập lại
nhiều lần. A lấy ví dụ về giải pháp khi mình thay đổi giá trị trong database thì nó tự động cập nhập giá trị đó lên các giao diện ứng dung
khác nhau như mobile , web, tivi cùng một lúc. Để giải quyết được vấn đề đó thì người ta áp dụng MVC pattern để giải quyết vấn đề.
Như vậy người ta áp dụng design pattern để giải quyết cho những vấn đề gặp phải ở nhiều tình huống khác nhau. Ngoài ra có có một chức năng cực quan trong là khi áp dụng design pattern khả năng mở rộng các chức năng ứng dụng rất cao. Ta không phải đập hết code củ để viết lại cái mới mà thay vào đó ta chỉ tạo thêm các Class mới và không xoá đi code củ.

<br>
# Tại sao nên sử dụng Design Pattern

1. Design Pattern giúp cho dự án chúng ta dể dàng mở rộng mà không phải xoá đi code. Chúng ta chỉ cần viết thêm Class mới cho
chức năng mới
2. Các mẫu Design Pattern này do các kỷ sư hàng đầu thế giới nghiêu cứu và phát triển nên ta hoàn toàn tin tưởng khả
năng mở rộng khi dùng chúng
3. Design Pattern như một ngôn ngữ chung mà tất cả developers trên thế giới đều biết , giúp chúng ta hiểu được các
thiết kế hệ thống của các developer

<br>
# Các loại design pattern hiện nay
Design Pattern được chia làm 3 mục chính là : <b>Creational Pattern</b> ( nhóm khởi tạo), <b>Structural </b>(nhóm cấu trúc) và <b>Behavioral</b> patterns (nhóm hành vi ) .

<b>Creational Pattern</b> ( nhóm khởi tạo): Nhóm này sẽ giúp bạn rất nhiều trong việc khởi tạo đối tượng. Nó gồm các design pattern sau. Mỗi loại design sẽ ứng với một mục đích khác nhau. Ứng dụng mỗi design pattern sẽ được miêu tả chi tiết và cụ thể trong các bài viết trong blog.

1. Abstract Factory.
2. Builder.
3. Factory Method.
4. Multiton.
5. Pool.
6. Prototype.
7. Simple Factory.
8. Singleton
10. Static Factory.

Vậy khi nào chúng ta dùng design pattern cho nhóm khởi tạo. Khởi tạo ở đây là việc tạo ra một đối tượng. Tại sao trong lập trình mình có thể dùng toán tử new để khai báo ra một đối tượng luôn. Dùng design pattern creation để làm gì? Câu trả lời rất đơn giản, chúng ta hoàn toàn có thể dùng từ khoá new để tạo ra đối tượng, nhưng ứng dụng của chúng ta sẽ không thể mở rộng trong tương lai. Nhiều lúc khi phát triển tính năng mới ta phải đập hết code củ và viết lại một chức năng mới. Trong 10 cách tạo đối tượng ở trên mỗi pattern sẽ có một vai trò , mục đích khác nhau. Tuỳ vào nghiệp vụ của chương trình mà ta có thể chọn pattern đúng để tạo ra các đối tượng giúp cho việc mở rộng sau này được dể dàng.


<b>Structural</b> (nhóm cấu trúc): Nhóm này sẽ giúp chúng ta thiết lập, định nghĩa quan hệ giữa các đối tượng. Cấu trúc để tạo đối tượng, chúng ta có 11 design pattern cho việc cấu trúc một đối tượng. 

1. Adapter/ Wrapper.
2.    Bridge.
3.    Composite.
4.    Data Mapper.
5.    Decorator.
6.    Dependency Injection.
7.    Facade.
8.    Fluent Interface.
9.    Flyweight.
10.    Registry.
11.    Proxy

Khi nói về cấu trúc của một đối tượng và cách mình tạo ra cấu trúc đó như thế nào thì mình sẽ sử dụng Structural Pattern. Anh lấy ví dụ như mình có ứng dụng là xây dựng cây gia phả của họ hàng mình như sau


Như vậy mình phải tìm một cấu trúc để lưu trữ cây gia phả cho hợp lý, có nghĩa là mình dể dàng thêm, sửa, xoá các node trong cây gia phả. Như vậy ta phải tìm ra một cấu trúc linh hoạt, và trong trường hợp này mình dùng Composite design pattern để tạo ra cấu trúc lại các đối tượng trong chức năng của mình.


<b>Behavioral</b> patterns (nhóm hành vi): Nhóm này sẽ tập trung thực hiện các hành vi của đối tượng. Chúng ta có các design pattern sau.

1.    Chain Of Responsibilities.
2.    Command.
3.    Iterator.
4.    Mediator.
5.    Memento.
6.    Null Object.
7.    Observer.
8.    Specification.
9.    State.
10.   Strategy.
11.   Template Method.
12.   Visitor.

Chúng ta sử dụng Behavior pattern khi chúng ta tập trung vào việc xử lý các hành động, và dự đoán trước rằng các hành động này sẽ được thay đổi trong tương lai. Anh lấy ví dụ như trong các collection của java mình có các tập hợp như List, Set . Các tập hợp này đều có sẳn hàng duyệt các phần tử. Nhưng nếu cũng trong ứng dụng của anh có thêm mảng []. Thì cái mảng này các duyệt các phần tử khác với cách thức của List và Set. Như vậy anh phải suy nghỉ viết ra một pattern mà khi a truyền vào là mảng [], list, hay map. Thì nó đều lấy được các phần tử như nhau và dùng 1 phương thức như nhau. Trong thực tế thì anh sẽ sử dụng Iterator và hành động của anh là duyệt qua các phần tử. Không quan tâm đầu vào nó là gì.

<br>
# Tổng kết
Như các em thấy hầu hết các framework mà chúng ta đang dùng đều xây dựng dựa trên các design pattern . Vì nó có
khả năng mở rộng cao . Ứng với từng mục đích , từng bài toán mà ta sẽ sử dụng pattern tương ứng để giải quyết vấn đề .
