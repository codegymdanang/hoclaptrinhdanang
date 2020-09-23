---
layout: course-spring-core
title: Annotation Configure
slug : spring-annotation-configure
category: laptrinhspring
tags: [spring-core]
summery: Configure Annotation
image: /images/blog/spring.png
featureImage: /images/post/javacore/feature_di.png
description : Hiều cấu hình Configure Annotation trong lập trình Spring. Hướng dẫn sử dụng Configure Annotation trong lập trình Spring.
youtubeId: 0n8_2yG5F7I
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào bạn, trong bài viết hôm nay chúng ta sẽ nói cách sử dụng annotation Configure để cấu hình cho dự án Spring.
 
# **1. Giới thiệu @Configure Annotation**

Spring @Configuration là một thành phần trong spring core framework. @Configuration annotation chỉ ra rằng trong class đó có @Bean. Vì vậy khi Spring IoC quyét qua các Class mà có annotation là @Configuration nó sẽ hiểu trong Class đó có khai báo một số bean và vào đó tạo các bean

Thường những cấu hình file cấu hình dự án mình sẽ dùng annotation @Configuration để đánh dấu cho Spring IoC biết.

# **2. Khai báo @Configure Annotation**

- Chúng ta sử dụng annotation @Configuration để đánh dấu là Class đó là Class dùng để cấu hình và có các bean cấu hình trong đó.

{% highlight java linenos %}

import org.springframework.boot.SpringApplication;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

import com.companyname.projectname.customer.CustomerService;
import com.companyname.projectname.order.OrderService;

@Configuration
public class Application {

     @Bean
     public CustomerService customerService() {
         return new CustomerService();
     }
 
     @Bean
     public OrderService orderService() {
         return new OrderService();
     }
}

{% endhighlight %}

- Class Application trên được khai báo bằng Java. Nếu chuyển sang XML thì có dạng như sau

{% highlight java linenos %}

<beans>
        <bean id="customerService" class="com.companyname.projectname.CustomerService"/>
        <bean id="orderService" class="com.companyname.projectname.OrderService"/>
</beans>
{% endhighlight %}








