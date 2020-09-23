---
layout: course-spring-core
title: Vòng đời Bean
slug : bean-lifecycle
category: laptrinhspring
tags: [spring-core]
summery: Vòng đời Bean
image: /images/blog/spring.png
featureImage: /images/post/javacore/feature_di.png
description : Hiều vòng đời Bean trong lập trình Spring. Hiểu được Bean Lifecycle là gì. Hướng dẫn sử dụng Bean Lifecycle trong lập trình Spring.
youtubeId: 0n8_2yG5F7I
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào bạn, trong bài viết hôm nay chúng ta sẽ nói qua vòng đời của một bean được tạo ra và phá huỷ trong Spring container.

# **1 .InitializingBean and DisposableBean**

Trong Spring chúng ta có thể sử dụng InitializingBean and DisposableBean để can thiệp khi bean (đối tượng) được tạo ra và huỷ đi trong Spring IoC container. 

- Các beans mà cài đặt InitializingBean mình có thể can thiệp vào quá trình tạo bean bằng việc thêm các thay đổi trong hàm afterPropertiesSet() mà InitializingBean cung cấp cho mình

- Các beans mà cài đặt DisposableBean mình có thể can thiệt vào quá trình bean bị huỷ bằng cách thêm các dòng code vào phương thức destroy() mà DisposableBean cung cấp

# **2 .Cấu hình project**


# **3 .Cấu hình pom**

<br>
{% highlight xml linenos %}

<project xmlns="http://maven.apache.org/POM/4.0.0"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>net.javaguides.spring</groupId>
    <artifactId>spring-bean-lifecycle</artifactId>
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

# **4 .Ví dụ bean Database trước khi khởi tạo và huỷ**

<br>
{% highlight java linenos %}

import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

import org.springframework.beans.factory.DisposableBean;
import org.springframework.beans.factory.InitializingBean;
import org.springframework.stereotype.Component;

@Component
public class DatabaseInitiaizer implements InitializingBean, DisposableBean {

    private List < User > listOfUsers = new ArrayList < > ();

    @Override
    public void afterPropertiesSet() throws Exception {
        User user = new User(1, "User");
        User user1 = new User(2, "Admin");
        User user2 = new User(3, "SuperAdmin");

        listOfUsers.add(user);
        listOfUsers.add(user1);
        listOfUsers.add(user2);
        System.out.println("-----------List of users added in init() method ------------");
        for (Iterator < User > iterator = listOfUsers.iterator(); iterator.hasNext();) {
            User user3 = (User) iterator.next();
            System.out.println(user3.toString());
        }
        // save to database
    }

    @Override
    public void destroy() {
        // Delete from database
        listOfUsers.clear();
        System.out.println("-----------After of users removed from List in destroy() method ------------");
        for (Iterator < User > iterator = listOfUsers.iterator(); iterator.hasNext();) {
            User user3 = (User) iterator.next();
            System.out.println(user3.toString());
        }
        System.out.println("List is clean up ..");
    }
}





{% endhighlight %}






















