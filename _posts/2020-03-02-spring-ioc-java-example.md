---
layout: course-spring-core
title: Spring IOC Java Example
slug : spring-ioc-java-example
category: laptrinhspring
tags: [spring-core]
summery: Cấu hình IOC qua Java 
image: /images/blog/spring.png
featureImage: /images/post/javacore/feature_di.png
description : Sử dụng Cấu hình IOC qua Java trong lập trình Spring. Hiểu được Cấu hình IOC qua Java là gì. Hướng dẫn sử dụng Cấu hình IOC qua Java trong lập trình Spring.
youtubeId: 0n8_2yG5F7I
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào ban , chắc hẳn bạn cảm thấy khó hiểu về <b>Cấu hình IOC qua Java</b> ? Có phải bạn không rõ khái niệm của nó trong lập trình?

<br>
# **1 .Tạo dự án Maven**




# **2 .Thêm các thư viện Spring vào Maven**

{% highlight xml linenos %}

<project xmlns="http://maven.apache.org/POM/4.0.0"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>net.javaguides.spring</groupId>
    <artifactId>spring-ioc-example</artifactId>
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

# **3 .Cấu hình HelloWorld Spring Bean bằng Java**

{% highlight java linenos %}

package com.levunguyen.spring.ioc;

public class HelloWorld {
    private String message;

    public void setMessage(String message) {
        this.message = message;
    }

    public void getMessage() {
        System.out.println("My Message : " + message);
    }
}
{% endhighlight %}

# **4 .Cấu hình Metadata Java**

- Như bài 1 giới thiệu về Spring IOC container ta có thể dùng code Java để tạo các bean. Code Java bình thường như bước 3 chỉ là 1 lớp java thường để trở thành bean thì ta phải thêm các cấu hình bằng annotaion @ như sau:

{% highlight java linenos %}

package com.levunguyen.spring.ioc;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class AppConfig {

    @Bean
    public HelloWorld helloWorld() {
        HelloWorld helloWorld = new HelloWorld();
        helloWorld.setMessage("Hello World!");
        return helloWorld;
    }
}
{% endhighlight %}

- Chúng ta sử dụng @Congiguration và @Bean. Khi container load lên nó sẽ nhận biết các annotation @ này để tạo bean (đối tượng)

# **5 .Tạo Spring Container**

{% highlight java linenos %}

import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

public class Application {
    public static void main(String[] args) {
        AnnotationConfigApplicationContext  context = new AnnotationConfigApplicationContext(AppConfig.class);
        context.close();
    }
}

{% endhighlight %}

# **6 .Lấy đối tượng bean HelloWorld và gọi phương thức**

- Chúng ta sử dụng phương thức getBean để lây đối tượng bean từ container

{% highlight java linenos %}

import org.springframework.context.annotation.AnnotationConfigApplicationContext;

public class Application {
    public static void main(String[] args) {
        // ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
        AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);
        HelloWorld obj = (HelloWorld) context.getBean("helloWorld");
        obj.getMessage();
        context.close();
    }
}

{% endhighlight %}

- Kết quả ta nhận được là text : Hello World






