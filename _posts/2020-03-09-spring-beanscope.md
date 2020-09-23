---
layout: course-spring-core
title: Phạm vi hoạt động của bean
slug : bean-scope
category: laptrinhspring
tags: [spring-core]
summery: Bean Scope
image: /images/blog/spring.png
featureImage: /images/post/javacore/feature_di.png
description : Sử dụng Bean Scope trong lập trình Spring. Hiểu được Bean Scope là gì. Hướng dẫn sử dụng Bean Scope trong lập trình Spring.
youtubeId: 0n8_2yG5F7I
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào ban , chắc hẳn bạn cảm thấy khó hiểu về <b>Bean Scoper</b> là gì đúng không? Trong bài viết hôm nay chúng ta sẽ nói qua 6 phạm vi (scope) của một bean được tạo ra trong container.

Có bao giờ bạn tự hỏi các beans (đối tượng) được tạo ra như thế nào không và khi nào nó được tạo ra trong container. Các scope dưới đây sẽ mô tả rõ.


# **1 .Singleton Scope**

- Khi một bean được khai báo là Singleton thì bean đó là duy nhất trong Spring IoC và được share cho tất cả các beans khác nếu cần sử dụng nó. Như vậy ta chỉ cần tạo 1 bean duy nhất và sử dụng cho toàn hệ thống. Anh lấy ví dụng mình có 1 bean về connect database thì mình chỉ tạo 1 lần duy nhất. Các bean khác muốn dùng thì nhúng vào chứ không phải mình có 10 beans khác nhau dùng bean connect database thì mình tạo 10 bean database trong Spring IoC.

- Scope mặc định khi một bean được tạo ra là Singleton

- Định nghĩa Scope Singletion bằng XML


{% highlight xml linenos %}

<bean id="accountService" class="com.foo.DefaultAccountService"/>

<!-- the following is equivalent, though redundant (singleton scope is the default) -->
<bean id="accountService" class="com.foo.DefaultAccountService" scope="singleton"/>

{% endhighlight %}

- Định nghĩa Scope Singleton bằng Java base

{% highlight java linenos %}

@Configuration
public class AppConfiguration {

 @Bean
 @Scope("singleton") // default scope 
 public UserService userService(){
  return new UserService();
 }
}

{% endhighlight %}

# **2 .Prototype Scope**

Khác với Singleton scope, bean (đối) sẽ được tạo ra mới mỗi khi có một yêu cầu tạo bean. Như vậy mỗi lần gọi tới bean mà có scope là Prototype thì nó sẽ tạo ra một đối tượng (bean) trong Spring IoC container.

- Định nghĩa Scope Singletion bằng XML


{% highlight xml linenos %}

<bean id="accountService" class="com.foo.DefaultAccountService" scope="prototype"/>

{% endhighlight %}

- Định nghĩa Scope Singleton bằng Java base

{% highlight java linenos %}

@Configuration
public class AppConfiguration {

 @Bean
 @Scope("prototype")
 public UserService userService(){
  return new UserService();
 }
}

{% endhighlight %}

# **3 .Request Session Application và WebSocket Scope**

Những scope như request, session, application và websocket thì chỉ có tồn tại ở những ứng dụng là web application. Nếu ta sử dụng ở những ứng dụng Spring độc lập thì sẽ nhận được thông báo lỗi IllegalExection unknow bean scope vì ứng dụng này không phải là ứng dụng web nên không có scope nêu trên.

Để sử dụng được các scope trên thì chúng ta phải configure (cấu hình) dự án web thêm một vài thông số như thêm SpringDispatchServlet vào file cấu hình trong file web.xml trước khi sử dụng các scope trên

{% highlight xml linenos %}

<web-app>
    ...
    <filter>
        <filter-name>requestContextFilter</filter-name>
        <filter-class>org.springframework.web.filter.RequestContextFilter</filter-class>
    </filter>
    <filter-mapping>
        <filter-name>requestContextFilter</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>
    ...
</web-app>

{% endhighlight %}


# **4 .Request Scope**

- Cấu hình request scope cho XML

{% highlight xml linenos %}

<bean id="loginAction" class="com.foo.LoginAction" scope="request"/>

{% endhighlight %}

- Cấu hình request scope cho Java

{% highlight java linenos %}

@RequestScope
@Component
public class LoginAction {
    // ...
}

{% endhighlight %}

- Spring Container sẽ tạo bean(đối tương) LoginAction mới khi có một request(yêu cầu) từ ngừoi dùng. Sau khi request(yêu cầu) xử lý xong thì bean sẽ bị xoá đi


# **5 .Session Scope**

Scope session sẽ tồn tại chừng nào sesion ở HTTP. Nó sẽ bị xoá đi khỏi Spring IoC khi session ở web bị xoá hoặc hết hiệu lực

{% highlight xml linenos %}

<bean id="loginAction" class="com.foo.LoginAction" scope="session"/>

{% endhighlight %}

- Cấu hình request scope cho Java

{% highlight java linenos %}

@SessionScope
@Component
public class UserPreferences {
    // ...
}

{% endhighlight %}

# **5 .Application Scope**

Ápplication scope được tạo một lần cho toàn bộ ứng dụng web application. Application scope được chứa đựng như một ServletContext nó cũng gần tương tự như Singleton scope nhưng nó là singleton cho từng ServeletContext.

{% highlight xml linenos %}

<bean id="appPreferences" class="com.foo.AppPreferences" scope="application"/>

{% endhighlight %}

- Cấu hình request scope cho Java

{% highlight java linenos %}

@ApplicationScope
@Component
public class AppPreferences {
    // ...
}

{% endhighlight %}




