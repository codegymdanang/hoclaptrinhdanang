---
layout: course-goodcode
title: Clean Code Về Method
slug : clean-code-method
category: craftmanship
tags: [goodcode]
summery: Method
image: /images/blog/quality-code.png
description : Clean Code Method trong lập trình lập trình. Hiều clean code là gì, hướng dẫn cách sử dụng method đúng trong học lập trình.
youtubeId: aSDKxAUqcTc
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em, hôm nay anh sẽ trình bày chủ đề về viết phương thức (method) như thế nào là hiệu quả.

# **1. Tên phương thức  là động từ**

Một phương thức luôn luôn bắt đầu là một động từ. Chọn động từ càng sát với ý nghĩa của phương thức càng tốt.

- Code không tốt

{% highlight java  linenos %}

public void chicago() { 

}

{% endhighlight %}


- Code tốt

{% highlight java  linenos %}

public void goToChicago() { 

}

{% endhighlight %}

<br>
# **2. Mệnh đề Switch**

Nếu trong đoạn code có quá nhiều switch case thì nên thay thế bằng abstract factory pattern. Các em có thể xem lại bài [này](https://levunguyen.com/craftmanship/2020/05/06/su-dung-abstract-factory-design-pattern/)
về abstract factory là gì ?

- Code không tốt

{% highlight java  linenos %}

public class Example {

	private static final String COMMISSIONED = null;
	private static final String HOURLY = null;
	private static final String SALARIED = null;

	public Money calculatePay(Employee e) throws InvalidEmployeeType {
		switch (e.type) {
		case COMMISSIONED:
			return calculateCommissionedPay(e);
		case HOURLY:
			return calculateHourlyPay(e);
		case SALARIED:
			return calculateSalariedPay(e);
		default:
			throw new InvalidEmployeeType(e.type);
		}
	}

	private Money calculateCommissionedPay(Employee e) {
		// TODO Auto-generated method stub
		return null;
	}

	private Money calculateHourlyPay(Employee e) {
		// TODO Auto-generated method stub
		return null;
	}

	private Money calculateSalariedPay(Employee e) {
		// TODO Auto-generated method stub
		return null;
	}
}
{% endhighlight %}

- Code tốt

{% highlight java  linenos %}

public abstract class Employee {
	public abstract boolean isPayday();

	public abstract Money calculatePay();

	public abstract void deliverPay(Money pay);
}

public interface EmployeeFactory {
	public Employee makeEmployee(EmployeeRecord r) throws InvalidEmployeeType;
}

public class EmployeeFactoryImpl implements EmployeeFactory {
	public Employee makeEmployee(EmployeeRecord r) throws InvalidEmployeeType {
		switch (r.type) {
		case COMMISSIONED:
			return new CommissionedEmployee(r);
		case HOURLY:
			return new HourlyEmployee(r);
		case SALARIED:
			return new SalariedEmploye(r);
		default:
			throw new InvalidEmployeeType(r.type);
		}
	}
}
{% endhighlight %}

<br>
# **3. Small**

Phương thức phải ngắn. Thông thường 1 method không nên quá 20 dòng code.

- Code không tốt

{% highlight java  linenos %}

public class Example {

	public static String renderPageWithSetupsAndTeardowns(PageData pageData, boolean isSuite) throws Exception {

		...
			more than 50 lines here
	    ....

		if (isTestPage(pageData))
			includeSetupAndTeardownPages(pageData, isSuite);

		...
			more than 50 lines here
		....

		return pageData.getHtml()
	}

}
{% endhighlight %}

- Code tốt : Chúng ta nên tách isTestPage và includeSetupAndTeardownPages thành 2 methods riêng

{% highlight java  linenos %}

public class Example {

	private static boolean isTestPage(PageData pageData) {
		// TODO Auto-generated method stub
		return false;
	}

	private static void includeSetupAndTeardownPages(PageData pageData, boolean isSuite) {
		// TODO Auto-generated method stub

	}
}
{% endhighlight %}

<br>
# **4. Phương thức chỉ nên có 1 level abstraction**

Ví dụ như anh muốn gọi phương thức render (vẽ hình) của đối tượng Drawline bên dưới. Thì anh chỉ cần paint.render() . Chỉ sử dụng 1 dấu chấm thôi (paint.render), chứ không phải gọi nhiều tầng (nhiều dấm chấm) paint.render().getFullPath().getElement(). Mình chỉ nên sử dụng 1 tầng (1 dấm chấm).

- Code không tốt

{% highlight java  linenos %}

DrawLine draw = paint.render().getFullPath (suiteTeardown).getElement();

{% endhighlight %}


- Code tốt

{% highlight java  linenos %}

 DrawLine draw = paint.render(pagePath); 

}
{% endhighlight %}

<br>
# **5. Giá trị Boolean trong IF Else**

Là một thói quen xấu nếu chúng ta truyền giá trị boolean và trong một method. Chúng ta nên tách thành 2 methods riêng biệt như ví dụ sau đây.

- Code không tốt

{% highlight java  linenos %}
	
	public Booking book (Customer aCustomer, boolean isPremium) {
	      if(isPremium) 
	       // logic for premium book
	      else
	       // logic for regular booking
	}

{% endhighlight %}

- Code tốt

Chúng ta nên có 2 phương thức  premiumBooking và regularBooking riêng biệt

{% highlight java  linenos %}
	
	public Booking book (Customer aCustomer) {
	     
	}

	public setPremiumBook() {

	}

	public setRegularBook() {
		
	}

}

{% endhighlight %}


<br>
# **5. Sử dụng Try/Catch**

Chúng ta nên di chuyển các code trong try catch thành các method bên ngoài và nhóm lại. Như vậy code sẽ dể hiểu hơn và không quá rối cho người đọc

- Code chưa tốt


{% highlight java  linenos %}

public void delete(Page page)
{
    try
    {
    	startEngineen()
    	putTheKey();
    	fill();
    	run();
        
    }
    catch (Exception e)
    {
    	logError(f);
        logError(e);
    }
}

{% endhighlight %}


- Code tốt

{% highlight java  linenos %}

public void drivingCar()
{
    try
    {
        startEngineen();
    }
    catch (Exception e)
    {
        problem(e);
    }
}

private void startEngineen throws Exception {
    putTheKey();
    fill();
    run();
}

private void problem(Exception e) {    
    logError(f);
    logError(e);
}

{% endhighlight %}

<br>
# **6. Method nên làm 1 nhiệm vụ**

Mỗi method chỉ làm một việc duy nhất. Trong ví dụ dưới đây hàm print làm 2 nhiệm vụ là printBaner và lấy tạo độ. Như vậy là sai vì mỗi method chỉ làm một nhiệm vụ của nó. Hàm print nên chỉ làm việc của mình là in ra màn hình còn việc lấy tạo độ để một method khác lo.

- Code không tốt

{% highlight java  linenos %}

void print() {
  printBanner();
  Position position = new Position();
  position.setX();
  position.setY();

}
{% endhighlight %}

- Code tốt

{% highlight java  linenos %}

void print() {
  printBanner();
}

void getPosition() {
	//calculateTax
}

{% endhighlight %}

<br>
# **7. Chuyển tham số thành đối tượng**

Method nhiều nhất chỉ chứa 2 tham số. Nếu vượt quá 2 tham số thì chúng ta nên gọp các tham số đó lại thành một đối tượng. Trong ví dụ dưới đây
chúng ta thay thế các tham số x,y,radius thành đối tượng Point

- Code không tốt

{% highlight java  linenos %}

public class Example {
	
	Circle makeCircle(double x, double y, double radius);
	
}
{% endhighlight %}

- Code tốt

Chúng ta nên có 2 phương thức riêng biệt

{% highlight java  linenos %}

public class Example {
	
	Circle makeCircle(Point center, double radius);

}

{% endhighlight %}


<br>
# **8. Copy/Paste code**

Copy code và dán lại code vào nhiều chỗ khác nhau trong source code là một thói quen xấu. Trường hợp nếu mình có lỗi xảy ra thì mình không biết tìm lỗi đó ở đâu, vì mình đã copy nó quá nhiều chỗ. Trong một team phát triển phần mềm có rất nhiều lập trình viên làm việc chung với nhau trên 1 source do đó nếu mình copy code và dán vào thì người khác cũng rất khó để tìm lỗi. Đặt biệt trong giai bảo trì , nhiều code copy sẽ dẫn đến trường hợp khó khăn trong fix bug. Chúng ta nên sử dụng tool sonar chi tiết tại [đây](https://levunguyen.com/craftmanship/2020/08/04/su-dung-sonarqube/) để kiểm tra xem code chúng ta đã tốt chưa có bị trùng lập ở đâu không.


# **Tóm tắt**

Các cách trên đây thường được áp dụng khi mình viết một phương thức đúng chuẩn. Nếu tuân thủ các cách trên anh chắn chắn mọi người sẽ viết ra những dòng code đẹp, dễ đọc và để bảo trì trong tương lai.
