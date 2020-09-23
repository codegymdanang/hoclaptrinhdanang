---
layout: course-spring-web
title: Sử dụng Spring AOP Pointcut 
slug : spring-aop-pointcut
category: laptrinhspring
tags: [spring-web]
summery: AOP Pointcut
image: /images/blog/spring.png
featureImage: /images/post/javacore/feature_springaop.png
description : Sử dụng AOP Pointcut trong lập trình spring. Hiểu cơ chế hoạt động của AOP Pointcut thông qua các  ví dụ thực tế.
youtubeId: WNfuVJptPnQ
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**
Chào các em ,chủ để hôm nay chúng ta sẽ tìm hiểu về <b>AOP Pointcut</b> có ý nghĩa là gì nhé .

<br>
# **1. Spring AOP Pointcut là gì**

Trong bài ví dụ về aop advise các em thấy một nhược điểm là tất cả method trong class HijackAroundMethod đều phải chạy intercept MethodBeforeAdvice , AfterReturningAdvice. Nhưng trong thực tế không phải lúc nào mình cũng chạy hết tất cả các method cần ghi log. Mà ta chỉ mong muốn chạy một vài method thôi mà thôi. Để làm được việc này ta sử dụng Pointcut

Để sử dụng được AOP Pointcut chúng ta có các thành phần sau

- Advice 	: chạy trước khi phương thức được thực thi
- Pointcut 	: Chỉ ra phương thức nào được chạy
- Advisor	: các Advise và Pointcut được truyền vào proxy object	

<br>
# **2. Ví dụ chưa sử dụng AOP Pointcut**

- Bước 1 : Tạo lớp CustomerService như sau

{% highlight java  linenos %}

    public class CustomerService
{
	private String name;
	private String url;

	public void setName(String name) {
		this.name = name;
	}

	public void setUrl(String url) {
		this.url = url;
	}

	public void printName(){
		System.out.println("Customer name : " + this.name);
	}

	public void printURL(){
		System.out.println("Customer website : " + this.url);
	}

	public void printThrowException(){
		throw new IllegalArgumentException();
	}

}

{% endhighlight %}

- Bước 2 : Cấu hình các bean giống như bài aop-advise

{% highlight java  linenos %}

<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans-2.5.xsd">

	<bean id="customerService" class="com.levunguyen.CustomerService">
		<property name="name" value="Le Vu Nguyen" />
		<property name="url" value="https://levunguyen.com" />
	</bean>

	<bean id="hackAroundMethodBeanAdvice" class="com.levunguyen.HackAroundMethod" />

	<bean id="customerServiceProxy"
                class="org.springframework.aop.framework.ProxyFactoryBean">

		<property name="target" ref="customerService" />

		<property name="interceptorNames">
			<list>
				<value>hackAroundMethodBeanAdvice</value>
			</list>
		</property>
	</bean>
</beans>

{% endhighlight %}

- Bước 3 : Chúng ta tạo lớp HackAroundMethod implement interface MethodInterceptor.
Chúng ta sử dụng method proceed để gọi phương thức chạy.

{% highlight java  linenos %}

import java.util.Arrays;
import org.aopalliance.intercept.MethodInterceptor;
import org.aopalliance.intercept.MethodInvocation;

public class HijackAroundMethod implements MethodInterceptor {
	@Override
	public Object invoke(MethodInvocation methodInvocation) throws Throwable {

		System.out.println("Method name : "
				+ methodInvocation.getMethod().getName());
		System.out.println("Method arguments : "
				+ Arrays.toString(methodInvocation.getArguments()));

		System.out.println("HijackAroundMethod : Before method hacked!");

		try {
			Object result = methodInvocation.proceed();
			System.out.println("HijackAroundMethod : Before after hacked!");

			return result;

		} catch (IllegalArgumentException e) {

			System.out.println("HijackAroundMethod : Throw exception hacked!");
			throw e;
		}
	}
}

{% endhighlight %}

- Bước 4 : Chúng ta test chương trình

{% highlight java  linenos %}

public class App {
	public static void main(String[] args) {
		ApplicationContext appContext = new ClassPathXmlApplicationContext(
				new String[] { "Spring-Customer.xml" });

		CustomerService cust = (CustomerService) appContext
				.getBean("customerServiceProxy");

		System.out.println("*************************");
		cust.printName();
		System.out.println("*************************");
		cust.printURL();
		System.out.println("*************************");
		try {
			cust.printThrowException();
		} catch (Exception e) {
		}
	}
}

{% endhighlight %}

Kết quả chúng ta nhận được là 

{% highlight java  linenos %}

*************************
Method name : printName
Method arguments : []
HijackAroundMethod : Before method hacked!
Customer name : Le Vu Nguyen
HijackAroundMethod : Before after hacked!
*************************
Method name : printURL
Method arguments : []
HijackAroundMethod : Before method hacked!
Customer website : https://levunguyen.com
HijackAroundMethod : Before after hacked!
*************************
Method name : printThrowException
Method arguments : []
HijackAroundMethod : Before method hacked!
HijackAroundMethod : Throw exception hacked!

{% endhighlight %}

# **3. Sử dụng AOP Pointcut**

Bước 1	: Tạo bean có tên là NameMatchMethodPointcut và đưa vào tên method mà ta muốn chạy. Trong ví dụ này chúng ta chỉ muốn chạy một mình phương thức printName thôi. Chúng ta khai báo phương thức printName trong thuộc tính mappedName như sau

{% highlight java  linenos %}

<bean id="customerPointcut"
        class="org.springframework.aop.support.NameMatchMethodPointcut">
	<property name="mappedName" value="printName" />
</bean>

{% endhighlight %}

- Bước 2	: Tạo bean DefaultPointcutAdvisor gồm có 2 beans là customerPointcut và hackAroundMethodBeanAdvice

{% highlight java  linenos %}

<bean id="customerAdvisor"
	class="org.springframework.aop.support.DefaultPointcutAdvisor">
	<property name="pointcut" ref="customerPointcut" />
	<property name="advice" ref="hijackAroundMethodBeanAdvice" />
</bean>

{% endhighlight %}

- Bước 3 : Thay đổi cấu hình của customerServiceProxy trỏ tới customerAdvisor

{% highlight java  linenos %}

<bean id="customerServiceProxy"
	class="org.springframework.aop.framework.ProxyFactoryBean">

	<property name="target" ref="customerService" />

	<property name="interceptorNames">
		<list>
			<value>customerAdvisor</value>
		</list>
	</property>
</bean>

{% endhighlight %}

- Bước 3 : Chạy lại test thì ta có kết quả sau

{% highlight java  linenos %}

*************************
Method name : printName
Method arguments : []
HijackAroundMethod : Before method hacked!
Customer name : Le Vu Nguyen
HijackAroundMethod : Before after hacked!
*************************
Customer website : https://levunguyen.com
*************************
{% endhighlight %}

Như các em thấy chỉ có một phương thức printName được in ra màn hình các phương thức như printURL thì không được in ra. Vì ta chỉ muốn chạy một mình phương thức printName

# **4. Sử dụng AOP Pointcut với Regular Expression**

Chúng ta có thể sử dụng regular expression để gán cho tên phương thức nào sẽ chạy pointcut. Như trong ví dụ dưới đây bất cứ phương thức nào có xuất hiện từ URL sẽ được chạy pointcut.

Bước 1 : Tạo RegexpMethodPointcutAdvisor

{% highlight java  linenos %}

<bean id="customerAdvisor"
	class="org.springframework.aop.support.RegexpMethodPointcutAdvisor">
	<property name="patterns">
		<list>
			<value>.*URL.*</value>
		</list>
	</property>

	<property name="advice" ref="hackAroundMethodBeanAdvice" />
</bean>
{% endhighlight %}
