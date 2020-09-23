---
layout: course-spring-core
title: Annotation Import
slug : spring-annotation-import
category: laptrinhspring
tags: [spring-core]
summery: Import Annotation
image: /images/blog/spring.png
featureImage: /images/post/javacore/feature_di.png
description : Hiều cấu hình Import Annotation trong lập trình Spring. Hướng dẫn sử dụng Import Annotation trong lập trình Spring.
youtubeId: 0n8_2yG5F7I
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào bạn, Trong bài viết hôm nay chúng ta sẽ nói cách sử dụng annotation Import để cấu hình cho dự án Spring.
 

# **1. Giới thiệu @Import Annotation**

Chúng ta sử dụng annotation Import khi muốn có một hoặc nhiều class cấu hình sẽ được import (nhúng vào) class.

# **2. Sử dụng import bằng XML**

Ví dụ ta có file xml sau là web.xml. Trong file web.xml này ta muốn nhúng các file xml khác là spring-common.xml, spring-dao.xml và spring-beans. 

Thì ta dùng thẻ <import>

{% highlight java linenos %}

<beans xmlns="http://www.springframework.org/schema/beans"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xsi:schemaLocation="http://www.springframework.org/schema/beans
 http://www.springframework.org/schema/beans/spring-beans.xsd">

 <import resource="common/spring-common.xml"/>
        <import resource="dao/spring-dao.xml"/>
        <import resource="beans/spring-beans.xml"/>
 
</beans>

{% endhighlight %}


# **2. Sử dụng import bằng annotation**

{% highlight java linenos %}

@Configuration
public class Common {

    @Bean
    public Share share() {
        return new Share();
    }
}

@Configuration
public class Dao {

    @Bean
    public Connection connect() {
        return new Connection();
    }
}


@Configuration
@Import(value = {Common.class,Dao.class } )
public class Web {

    @Bean
    public Page page() {
        return new Page();
    }
}

{% endhighlight %}






