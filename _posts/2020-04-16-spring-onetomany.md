---
layout: course-spring-web
title: Sử dụng OneToMany Relationship
slug : one-to-many
category: laptrinhspring
tags: [spring-web]
summery: OneToMany 
image: /images/blog/spring.png
featureImage: /images/post/javacore/feature_manytomany.png
description : Sử dụng @OneToMany mapping trong lập trình Spring. Hướng dẫn sử dụng annotation @onetomany trong spring data jpa.
youtubeId: JSnxij3p6nU
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em ,chủ đề hôm nay chúng ta sẽ nói về các annotation <b>@OneToMany</b> và <b>@ManyToOne</b> trong Spring  .


<br>
# **1. One To Many annotation**

Anh lấy ví dụ như mình làm ứng dụng về bán hàng. Mình có chức năng thêm sản phẩm (Item)  vào  giỏ hàng (cart) .
Trong giỏ hàng (cart) sẽ chứa nhiều sản phẩm (Items). Như vậy quan hệ giữa giỏ hàng và sản phẩm  là One To Many nghĩa là 1 giỏ hàng chứa nhiều sản  phẩm.

Nếu ta thiết kết database thì ta có 2 bảng là cart và item như sau .

{% highlight mysql  linenos %}
CREATE TABLE `Cart` (
  `cart_id` int(11) unsigned NOT NULL AUTO_INCREMENT,
  PRIMARY KEY (`cart_id`)
) ENGINE=InnoDB AUTO_INCREMENT=5 DEFAULT CHARSET=utf8;

CREATE TABLE `Items` (
  `id` int(11) unsigned NOT NULL AUTO_INCREMENT,
  `cart_id` int(11) unsigned NOT NULL,
  PRIMARY KEY (`id`),
  KEY `cart_id` (`cart_id`),
  CONSTRAINT `items_ibfk_1` FOREIGN KEY (`cart_id`) REFERENCES `Cart` (`cart_id`)
) ENGINE=InnoDB AUTO_INCREMENT=7 DEFAULT CHARSET=utf8;
{% endhighlight %}


Như vậy mối quan hệ trong database giữa Cart và Item là một nhiều . Column cart_id là khoá chính trong bảng Cart và là khoá phụ trong bảng Items.

Trong Java mình thể hiện mối quan hệ 1 - nhiều qua annotation <b>@OneToMany</b>. Ví dụ như ta khai báo lớp Cart có quan hệ một nhiều với lớp Item như sau.

{% highlight java   linenos %}
public class Cart {

    @OneToMany(mappedBy="cart")
    private Set<Items> items;

}
{% endhighlight %}

Chúng ta sử dụng annotation <b>@OneToMany</b> để nói lên mối liên hệ một nhiều. Như ví dụ trên ta có thể thấy 1 giỏ hảng (Cart) có nhiều sản phẩm Items. Ở trên chúng ta sử dụng collection là Set vì chúng ta muốn tập hợp sản phẩm không được trùng lập nhau. Các em có thể sử dụng các tập hợp khác như List , Map cũng được. Tuỳ theo mục đích sử dụng mà mình chọn tập hợp cho đúng

<br>
# **2. Triển khai trong Java code

Bây giờ anh sẽ hướng dẫn các bạn xây dựng ứng dụng shopping cart . Sử dụng <b>@OneToMany và @ManyToOne</b> để thiết lập mối quan hệ giữa
Cart (gio hang) và Item (san phẩm).

<br>
#### Bước 1. Tạo các tables : Cart và Item

{% highlight mysql  linenos %}
CREATE TABLE `Cart` (
  `cart_id` int(11) unsigned NOT NULL AUTO_INCREMENT,
  PRIMARY KEY (`cart_id`)
) ENGINE=InnoDB AUTO_INCREMENT=5 DEFAULT CHARSET=utf8;

CREATE TABLE `Items` (
  `id` int(11) unsigned NOT NULL AUTO_INCREMENT,
  `cart_id` int(11) unsigned NOT NULL,
  PRIMARY KEY (`id`),
  KEY `cart_id` (`cart_id`),
  CONSTRAINT `items_ibfk_1` FOREIGN KEY (`cart_id`) REFERENCES `Cart` (`cart_id`)
) ENGINE=InnoDB AUTO_INCREMENT=7 DEFAULT CHARSET=utf8;
{% endhighlight %}

<br>
#### Bước 2. Thêm dependency trong maven

{% highlight java linenos %}
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-jpa</artifactId>
        </dependency>

         <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <scope>runtime</scope>
         </dependency>

{% endhighlight %}

<br>
#### Bước 3. Tạo Entity Cart

{% highlight java   linenos %}
@Entity
@Table(name="CART") // tên này trùng với tên Table trong database .
public class Cart {

    //...

    @OneToMany(mappedBy="cart") // chú ý biến cart này được khai báo trong Class Item bên dưới. Chúng phải giống y chang nhau cái tên
    private Set<Items> items;

    public Set<Items> getItems () {
      return items ;
    }
}
{% endhighlight %}

Chúng ta chú ý, theo yêu cầu thì một giỏ hàng (Cart) sẽ chứa nhiều sản phẩm giống như trong database mô tả . Để làm được việc đó
Ta sử dụng <b>@OneToMany</b> trong Class Cart, điều đó có nghĩa 1 giỏ hàng sẽ có nhiều sản phẩm (Items) .

Tiếp đến ta sẽ thấy từ mappedBy = "cart". <b>MappedBy</b> dùng để đinh nghĩa Class Cart và Class Item sẽ liên kết với nhau thông qua tên "cart".
Và bắt buộc tên "cart" phải được định nghĩa trong Class Item. MappedBy giống như là 1 cầu nối để ta có thể từ Class Cart mình gọi hàm getItems mình sẽ nhận được một danh sách Items

<br>
#### Bước 4. Tạo Entity Items

{% highlight java   linenos %}
@Entity
@Table(name="ITEMS")
public class Items {

    //...
    @ManyToOne
    @JoinColumn(name="cart_id", nullable=false) //cart_id chính là trường khoá phụ trong table Item liên kết với khoá chính trong table Cart
    private Cart cart;

    public Items() {}

    // getters and setters
}
{% endhighlight %}

Chúng ta thấy trong lớp Cart chúng ta định nghĩa <b>@OneToMany</b> và <b>mappedBy</b> với  giá trị "cart" để tạo liên kết giữa lớp Cart và Item  . Để liên kết
đó hoạt động thì ta cũng phải cấu hình biến "cart" trong Class Item.

Đầu tiên chúng ta sử dụng  @ManyToOne và <b>@JoinColumn</b> để định nghĩa cho biến cart để tạo sự liên kết ngược lại  giữa Class Items và Cart  .
.Trong @JoinColumn ta định nghĩa name = "car_id" . Cái 'cart_id ' chính là  column khoá phụ trong table Items mà ta định nghĩa trong database . nullable = false là ta ràng buộc dữ liệu không được phép null

<br>
#### Bước 5. Test ứng dụng

Chúng ta sẽ lưu giỏ hàng và các sản phẩm xuống database theo cách sau. Khi dữ liệu được lưu thì nó sẽ được lưu xuống cả 2 tables cùng một lúc.


{% highlight java   linenos %}

 Items item1 = new Items ("Item 1");
 Items item2 = new Items ("Item 2");
 Set<Items> items = new HashSet<Items>();
 items.add(item1);
 items.add(item2);

 Cart cart = new Cart();
 cart.setItems(items);
 cart.save(); // như vậy ta sẽ lưu dữ liệu xuống 2 bảng Cart và Items


{% endhighlight %}

<br>
# **3. Kết luận**

Như vậy chúng ta sử dụng annotaion @OneToMany và @ManyToOne để thực hiện việc liên kết giữa hai entity với nhau. Trong lập trình sẽ có những lúc khi ta có thể query từ Cart lấy ra tất cả các dòng dữ liệu Items trong Cart đó hoặc sẽ có những trường hợp ngược lại là từ những Items trong Cart đó ta có thể lấy được Cart đó là gì thông qua các Item. Đó chính là Bidirectional chúng ta có thể query Cart lấy Item hoặc query ngược từ Item ra Cart. Để làm được việc này thì ta phải sử dụng @JoinColumn và MappedBy để thực hiện Bidriectional 


{:refdef: style="text-align: center;"}
{% include youtubePlayer.html id=page.youtubeId %}
{: refdef}