---
layout: course-spring-core
title: Annotation Lazy
slug : spring-annotation-lazy
category: laptrinhspring
tags: [spring-core]
summery: Lazy Annotation
image: /images/blog/spring.png
featureImage: /images/post/javacore/feature_di.png
description : Hiều cấu hình Lazy Annotation trong lập trình Spring. Hướng dẫn sử dụng Lazy Annotation trong lập trình Spring.
youtubeId: 0n8_2yG5F7I
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào bạn, Trong bài viết hôm nay chúng ta sẽ nói cách sử dụng annotation Lazy để cấu hình cho dự án Spring.
 

# **1. Giới thiệu @Lazy Annotation**

Mặc định khi Spring IoC bật lên (start) nó sẽ tạo các beans mà ta khai báo. Tuy nhiên chúng ta hoàn toàn có thể nói cho Spring IoC không khởi tạo các bean ngay mà khởi tạo khi ta cần dùng thông qua annotaion @Lazy.

Chúng ta hãy xem ví dụ sau


# **2. Tạo maven**


{% highlight xml linenos %}

<project xmlns="http://maven.apache.org/POM/4.0.0"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
 <modelVersion>4.0.0</modelVersion>
 <groupId>net.javaguides.spring</groupId>
 <artifactId>spring-lazy-annotation</artifactId>
 <version>0.0.1-SNAPSHOT</version>
 <url>http://maven.apache.org</url>

 <properties>
  <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
 </properties>

 <dependencies>
  <!-- https://mvnrepository.com/artifact/org.springframework/spring-context -->
  <dependency>
   <groupId>org.springframework</groupId>
   <artifactId>spring-context</artifactId>
   <version>5.1.0.RELEASE</version>
  </dependency>

 </dependencies>
 <build>
  <sourceDirectory>src/main/java</sourceDirectory>
  <plugins>
   <plugin>
    <artifactId>maven-compiler-plugin</artifactId>
    <version>3.5.1</version>
    <configuration>
     <source>1.8</source>
     <target>1.8</target>
    </configuration>
   </plugin>
  </plugins>
 </build>
</project>

{% endhighlight %}

# **3. Tạo java class**

- Trong ví dụ hôm nay chúng ta tạo 2 beans là Bean1 và Bean2
<br>
{% highlight java linenos %}

public class FirstBean {

    public FirstBean() {
        System.out.println("Bean1");
    }

    public void test() {
        System.out.println("Bean1");
    }
}

{% endhighlight %}

<br>
{% highlight java linenos %}

public class SecondBean {

    public SecondBean() {
        System.out.println("Bean2");
    }

    public void test() {
        System.out.println("Bean2");
    }
}

{% endhighlight %}


# **4. Tạo 2 beans class**

- Chú ý trong class Configure này anh sử dụng annotation @Lazy cho Bean1. Như vậy khi Spring IoC khởi động Bean1 sẽ chưa được tạo ngay mà Bean2 tạo trước

<br>
{% highlight java linenos %}

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.Lazy;

@Configuration
public class AppConfig {

    @Lazy(value = true)
    @Bean
    public FirstBean firstBean() {
        return new FirstBean();
    }

    @Bean
    public SecondBean secondBean() {
        return new SecondBean();
    }
}
{% endhighlight %}

# **5. Chạy Test**

<br>
{% highlight java linenos %}

import org.springframework.context.annotation.AnnotationConfigApplicationContext;

public class Application {
    public static void main(String[] args) {
        AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);
        FirstBean firstBean = context.getBean(FirstBean.class);
        firstBean.test();
        context.close();
    }
}

{% endhighlight %}

- Kết quả sẽ in ra là :  Bean2 , Bean 1
Như vậy ta thấy Bean1 chỉ được gọi khi cần, và chỉ được tạo lên khi cần thông qua @Lazy









