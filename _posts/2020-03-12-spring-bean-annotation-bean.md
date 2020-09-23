---
layout: course-spring-core
title: Annotation @Bean
slug : spring-annotation-bean
category: laptrinhspring
tags: [spring-core]
summery: Bean Annotation
image: /images/blog/spring.png
featureImage: /images/post/javacore/feature_di.png
description : Hiều cấu hình @Bean Annotation trong lập trình Spring. Hướng dẫn sử dụng @Bean Annotation trong lập trình Spring.
youtubeId: 0n8_2yG5F7I
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào bạn, Trong bài viết hôm nay chúng ta sẽ nói cách sử dụng annotation bean để cấu hình cho dự án Spring.
 
# **1. Giới thiệu @Bean Annotation**

Trong các bài trước về tạo bean trong XML chúng ta sử dụng thẻ <bean /> tạo tạo một bean trong Spring IoC. Ngoài cách tạo bằng XML thì chúng ta có thể hoàn toàn tạo bean bằng sử dung annotation @Bean

# **2. Khai báo bean bằng cách sử dụng @Bean**


- Tạo bean sử dụng annotation @Bean

{% highlight java linenos %}

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

- Tạo bean bằng xml

{% highlight xml linenos %}

<beans>
        <bean id="customerService" class="com.companyname.projectname.CustomerService"/>
        <bean id="orderService" class="com.companyname.projectname.OrderService"/>
</beans>

{% endhighlight %}

# **3. Vòng đời @Bean**

Annotation @Bean cũng hỗ trợ chức năng initialization và destruction giống như trong Spring XML là init-method và destroy-method
<br>
{% highlight java linenos %}

public class Foo {
        public void init() {
                // initialization logic via xml config
        }
}

public class Bar {
        public void cleanup() {
                // destruction logic via xml config
        }
}

@Configuration
public class AppConfig {

        @Bean(initMethod = "init")
        public Foo foo() {
                return new Foo();
        }

        @Bean(destroyMethod = "cleanup")
        public Bar bar() {
                return new Bar();
        }

}
{% endhighlight %}

# **4.Thay đổi tên của bean**

chúng ta sử dụng thuộc tính name để đặt tên cho bean
<br>
{% highlight java linenos %}
@Configuration
public class Application {

 @Bean(name = "cService")
 public CustomerService customerService() {
  return new CustomerService();
 }
 
 @Bean(name = "oService")
 public OrderService orderService() {
  return new OrderService();
 }
}
{% endhighlight %}

















