---
layout: course-spring-core
title: Spring IOC Container
slug : spring-ioc-container
category: laptrinhspring
tags: [spring-core]
summery: Spring IOC Container  
image: /images/blog/spring.png
featureImage: /images/post/javacore/feature_di.png
description : Sử dụng Spring IOC Container trong lập trình Spring. Hiểu được Spring IOC Container là gì. Hướng dẫn sử dụng Spring IOC Container trong lập trình Spring.
youtubeId: 0n8_2yG5F7I
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào ban , chắc hẳn bạn cảm thấy khó hiểu về <b>Spring IOC Container</b> (DI) là gì đúng không? Có phải bạn không rõ khái niệm của nó trong lập trình?
Tại sao chúng ta cần Spring IOC Container ? Và cuối cùng là lợi ích khi sử dụng <b>Spring IOC Container</b>. 

<br>
# **1 .Spring IOC Container**

Trong tất cả các dự án Spring thì Spring IOC Container là trái tim của Spring. Nó có nhiệm vụ quản lý vòng đời của bean (các đối tượng trong dự án spring), khởi tạo, cấu hình, và tương tác giữa các bean trong ứng dụng Spring. Mình có thể cấu hình Spring IOC bằng XML, Java code hoặc quan Java annotaion.

Spring framework hỗ trợ 2 loại container là BeanFactory container và ApplicationContext container. Giúp chúng ta có thể khởi tạo và quản lý các beans (đối tượng) trong Spring

BeanFactory là interface trên cùng của Spring IOC container còn ApplicationContext là lớp con của BeanFactory. Sự khác nhau chính của BeanFactory và ApplicationContext là 

- BeanFactory : Các bean được tạo ra khi chúng ta gọi phương thức getBean()

- ApplicationContext : chúng ta không cần phải chờ phương thức getBean được gọi mới tạo Bean. Mà khi container được start (khởi động) thì bean cũng đã được tạo ra do vậy không phải chờ gọi phương thức getBean.


# **2 .Khởi tạo Spring Container**

Có 3 cách khởi tạo Spring Container như sau :

- AnnotationConfigApplicationContext : Sử dụng khi chúng ta viết 1 chương trình Java độc lập. Không phải là Java web mà chỉ là ứng dụng java thông thường.

- ClassPathXmlApplicationContext : Nếu như ta sử dụng XML để cấu hình cho Spring thì ta dùng ClassPathXmlApplicationContext để nạp các cấu hình đó thông qua file XML

- FileSystemXmlApplicationContext : Cũng tương tự như ClassPathXmlApplicationContext nhưng file cấu hình chúng ta không phải là XML và chúng ta chỉ định đường dẫn để nạp file đó là ở đâu

- Ví dụ như ta sử dụng ApplicationContext để tạo Spring Container cho ứng dụng Java độc lập như sau. Giả sử ta đã có file applicationContext.xml rồi.


{% highlight java linenos %}

ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");

{% endhighlight %}

# **3 .Lấy beans từ SpringContainer bằng ApplicationContext**

Spring Container là nơi chứa đựng tất cả các beans (đối tượng) của ứng dụng trong 1 chương trình. Mỗi bean sẽ có 1 cái tên riêng. Dựa vào cái tên đó ta có thể lấy được đối tượng tương ứng với tên.


{% highlight java linenos %}

ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml"); 
HelloWorld obj = (HelloWorld) context.getBean("helloWorld");

{% endhighlight %}

- Bước 1 : ta khởi tạo Spring Container bằng cách đọc file applicationContext.xml ClassPathXmlApplicationContext("applicationContext.xml") Như vậy trong file applicationContext.xml sẽ có tất cả các bean trong đó giả sử ta có 1 bean tên là helloWorld. Ta sẽ lấy ra ở bước 2

- Bước 2 : ta sử dụng phương thức context.getBean("bean name") lúc này container sẽ trả lại cho mình 1 đối tượng như mình muốn context.getBean("helloWorld");

# **3 .Lấy beans từ SpringContainer bằng BeanFactory**

{% highlight java linenos %}

XmlBeanFactory factory = new XmlBeanFactory (new ClassPathResource("beans.xml")); 
HelloWorld obj = (HelloWorld) factory.getBean("helloWorld"); 

{% endhighlight %}



