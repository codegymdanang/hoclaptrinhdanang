---
layout: course-spring-core
title: Tổng hợp các Annotation
slug : spring-core-annotation-collection
category: laptrinhspring
tags: [spring-core]
summery: Các Annotation Spring Core
image: /images/blog/spring.png
featureImage: /images/post/javacore/feature_di.png
description : Tổng hợp các Annotation trong lập trình Spring. Hướng dẫn sử dụng  Annotation trong lập trình Spring.
youtubeId: 0n8_2yG5F7I
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào bạn, Trong bài viết hôm nay chúng ta sẽ tổng hợp các  annotation trong Spring Core

# **1. @Autowire Annotation**

Sử dụng để nhúng các bean vào bean cần dùng. Có thể nhúng qua Constructor , Setter và biến

- Constructor

{% highlight java linenos %}

@RestController
public class CustomerController {
    private CustomerService customerService;
 
    @Autowired
    public CustomerController(CustomerService customerService) {
        this.customerService = customerService;
    }
}

{% endhighlight %}

- Setter

{% highlight java linenos %}

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class CustomerController {
    private CustomerService customerService;
 
    @Autowired
    public void setCustomerService(CustomerService customerService) {
        this.customerService = customerService;
    }
}

{% endhighlight %}

- Field (biến)

{% highlight java linenos %}
@RestController
public class CustomerController {
    @Autowired
    private CustomerService customerService;
}

{% endhighlight %}


# **2. @Bean Annotation**

- Sử dụng để tạo các bean trong ứng dụng Spring

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

# **3. @Qualifier Annotation**

- Khi có nhiều Bean có cùng kiểu dữ liệu thì @Qualifier giúp chúng ta xát định nó là kiểu gì. Ví dụ như ta có 2 loại gửi tin nhắn là Email và SMS cùng implements 1 interface là Message Service. Chúng ta sử dụng @Qualifier để xát định đó là lại Email hay SMS vì chúng cùng 1 kiểu Message Service

{% highlight java linenos %}

public interface MessageService {
    public void sendMsg(String message);
}

{% endhighlight %}


{% highlight java linenos %}

public class EmailService implements MessageService{

    public void sendMsg(String message) {
         System.out.println(message);
    }
}

{% endhighlight %}

{% highlight java linenos %}

public class SMSService implements MessageService{

    public void sendMsg(String message) {
         System.out.println(message);
    }
}

{% endhighlight %}

{% highlight java linenos %}

public interface MessageProcessor {
    public void processMsg(String message);
}

public class MessageProcessorImpl implements MessageProcessor {

    private MessageService messageService;

    // setter based DI
    @Autowired
    @Qualifier("emailService")
    public void setMessageService(MessageService messageService) {
        this.messageService = messageService;
    }
 
    // constructor based DI
    @Autowired
    public MessageProcessorImpl(@Qualifier("emailService") MessageService messageService) {
        this.messageService = messageService;
    }
 
    public void processMsg(String message) {
        messageService.sendMsg(message);
    }
}
{% endhighlight %}

# **4. @Require Annotation**

Sử dụng @Require thường dùng ở phương thức setter nhầm bắt buộc phải nhúng giá trị vào

{% highlight java linenos %}

@Required
void setColor(String color) {
    this.color = color;
}

{% endhighlight %}

# **5. @Value Annotation**

Được sử dụng để lấy giá trị từ file properties
<br>
{% highlight java linenos %}

@Value("${APP_NAME_NOT_FOUND}")

private String defaultAppName;

{% endhighlight %}

# **6. @Lazy Annotation**

Sử dụng @Lazy để ngăn Spring IoC tạo bean, chỉ tạo khi mình cần.

{% highlight java linenos %}

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

# **7. @Primary Annotation**

Khi nhiều bean có cùng một kiểu (type). Chúng ta có quyền ưu tiên cho bean nào được load lên đầu tiên

{% highlight java linenos %}

@Component
@Primary
class Car implements Vehicle {}
 
@Component
class Bike implements Vehicle {}
 
@Component
class Driver {
    @Autowired
    Vehicle vehicle;
}
 
@Component
class Biker {
    @Autowired
    @Qualifier("bike")
    Vehicle vehicle;
}

{% endhighlight %}

# **7. @Scope Annotation**

Dùng để nói lên phạm vi tồn tại của một bean. 

{% highlight java linenos %}

@Component
@Scope(value = ConfigurableBeanFactory.SCOPE_SINGLETON)
public class TwitterMessageService implements MessageService {
}

@Component
@Scope(value = ConfigurableBeanFactory.SCOPE_PROTOTYPE)
public class TwitterMessageService implements MessageService {
}

{% endhighlight %}

# **8. @Import Annotation**

Dùng để nhúng 1 hoặc nhiều file configure lại với nhau.

{% highlight java linenos %}

@Configuration
public class ConfigA {

    @Bean
    public A a() {
        return new A();
    }
}

@Configuration
@Import(ConfigA.class)
public class ConfigB {

    @Bean
    public B b() {
        return new B();
    }
}
{% endhighlight %}

# **8. PropertySource**

Dùng để nạp các file properties từ bên ngoài vào bean

{% highlight java linenos %}

@Configuration
@PropertySource("classpath:config.properties")
public class ProperySourceDemo implements InitializingBean {

    @Autowired
    Environment env;

    @Override
    public void afterPropertiesSet() throws Exception {
        setDatabaseConfig();
    }

    private void setDatabaseConfig() {
        DataSourceConfig config = new DataSourceConfig();
        config.setDriver(env.getProperty("jdbc.driver"));
        config.setUrl(env.getProperty("jdbc.url"));
        config.setUsername(env.getProperty("jdbc.username"));
        config.setPassword(env.getProperty("jdbc.password"));
        System.out.println(config.toString());
    }
}
{% endhighlight %}









