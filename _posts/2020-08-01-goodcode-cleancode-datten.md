---
layout: course-goodcode
title: Clean Code cách đặt tên trong lập trình
slug : clean-code-dat-ten
category: craftmanship
tags: [goodcode]
summery: Qui tắc đặt tên
image: /images/blog/quality-code.png
description : Clean Code cách đặt tên trong lập trình lập trình. Hiều clean code là gì, hướng dẫn cách đặt tên đúng trong học lập trình.
youtubeId: aSDKxAUqcTc
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em, hôm nay anh sẽ trình bày chủ đề về đặt tên biến ,hàm như thế nào là đúng. Khi mình viết code cái mình hướng tới là những dòng code của mình người khác đọc vào sẽ hiểu ý định mình là làm gì? Trải qua 10 năm làm code cái anh nhận thấy đa số các lập trình viên viết code chủ yếu là mình hiểu, còn người khác thì đọc chưa chắc đã hiểu. Chính vì vậy thường các lập trình viên khi đọc code người khác mà không hiểu thường sẽ xoá code đó đi và viết lại code mới. Điều này rất nguy hiểm vì nếu mình xoá nhầm một dòng code quan trọng thì chương trình có thể chạy sai. Chính vì vậy hôm nay anh sẽ hướng dẫn mọi người cách đặt tên cho đúng.

# **1. Chọn một từ cho một khái niệm**

Ví dụ trong ứng dụng của mình. Mình có chức năng là lấy danh sách các nhân viên có trong công ty.
Mình có thể đặt tên method là getEmployee hoặc retrieveEmployee. Hai từ này điều có nghĩa là lấy danh sách nhân viên. Nhưng trong khi lập trình mình nên thống nhất một từ là get hoặc retrieve cho toàn bộ hệ thống để tránh sự nhầm lẫn. Không nên lúc thì gọi là getEmployee , lúc thì gọi retrieveEmployee. Như vây quy tắc đầu tiên nên chọn một từ duy nhất để mô tả chức năng của hệ thống.

Đoạn code dưới đây là không tốt. Mình nên chọn một cái tên là get hoặc retrieve mà thôi.

{% highlight java  linenos %}
public class Example {

	//choose only one concept

	public List<Employee> getEmployees() {
		return null;
	}

	public List<Employee> retrieveEmployees() {
		return null;
	}


}
{% endhighlight %}

<br>
# **2. Đặt tên phải tìm kiếm được**

Đoạn code dưới đây là không tốt vì khi mình khai báo biến String s, lúc này khi mình tìm kiếm cái biến s thì nó sẽ xuất hiện ra cả ngàn file chứ chữ s. Rất khó khăn trong việc tìm kiếm.  

{% highlight java  linenos %}
public class Example1 {

	private static final int NUMBER_OF_TASKS = 0;

	public static void bad() {
		String s = null;
		int[] t = null;
		for (int j = 0; j < 34; j++) {
			s += (t[j] * 4) / 5;
		}
	}
}
{% endhighlight %}

Cũng là đoạn mã trên ta viết lại như sau. Như vậy thay vì khai báo chữ s. Ta sẽ viết rõ ràng tên biến. Ví dụ như realTaskDays , như vậy khi ta tìm kiếm chỉ sẽ xuất hiện 1 file chứa từ khoá realTaskDays.

{% highlight java  linenos %}

public static void good() {
		int realDaysPerIdealDay = 4;
		int WORK_DAYS_PER_WEEK = 5;
		int sum = 0;
		for (int j = 0; j < NUMBER_OF_TASKS; j++) {
			int[] taskEstimate = null;
			int realTaskDays = taskEstimate[j] * realDaysPerIdealDay;
			int realdays = 0;
			int realTaskWeeks = (realdays / WORK_DAYS_PER_WEEK);
			sum += realTaskWeeks;
		}

	}
{% endhighlight %}

<br>
# **3. Đặt tên phải lộ ra ý định của nó là gì**

Ví dụ anh có đoạn mã sau. Khi đọc đoạn code này mình thực sự không biết hàm getThem() là làm gì?
biết list1 là ?

{% highlight java  linenos %}
public List<int[]> getThem() {
		List<int[]> list1 = new ArrayList<int[]>();
		for (int[] x : theList)
			if (x[0] == 4)
				list1.add(x);
		return list1;
	}
{% endhighlight %}

Cũng là đoạn mã trên nhưng anh viết lại thì mọi người sẽ dể dàng biết được ý định của anh là gì? Khi nhìn vào biếtn gameBoard mình có thể đoán ngay là doạn code sau đây đang viết về một ván cờ. Từ khoá Cell mình có thể đoán ngay là các ô trên bàn cờ.

{% highlight java  linenos %}
// good
	public List<int[]> getFlaggedCells() {
		List<int[]> flaggedCells = new ArrayList<int[]>();
		for (int[] cell : gameBoard)
			if (cell[STATUS_VALUE] == FLAGGED)
				flaggedCells.add(cell);
		return flaggedCells;
	}
{% endhighlight %}

<br>
# **4. Đặt tên phải thảo luận được và đọc được**

Trong lập trình khi có một vấn đề gì đó thì chúng thường thảo luận với nhau. Nếu như ta đặt tên biên mà không phát âm được như đoạn code sau thì không cách nào mình có thể thảo luận với đồng nghiệp mà giải quyết được vấn đề. Ví dụ cái biến genymdhms nó không thể phát âm được.

{% highlight java  linenos %}
public class Example1 {

	//A company I know has genymdhms (generation date, year, month, day, hour, minute, and second)

	private Date genymdhms
	private Date modymdhms;
	private final String pszqint = "102";
}
{% endhighlight %}

Chúng ta sẽ viết lại đoạn mã sau với chức năng tương tự. Cái biến genymdhms giờ đổi thành generationTimestamp. Như vậy chúng ta có thể phát âm và thảo luận được.

{% highlight java  linenos %}
public class Example1 {
	//good
	private Date generationTimestamp;
	private Date modificationTimestamp;
	private final String recordId = "102";
}
{% endhighlight %}

<br>
# **5. Đặt tên không nên hoa mỹ**

Ví dụ đoạn mã sau đây là xoá một dòng trong ứng dụng.

{% highlight java  linenos %}
public class Example {

	//tên rất hay nhưng không ai hiểu nó làm gì
	public void holyHandGrenade() {

	}
}
{% endhighlight %}

Thay vì đặt tên hay nhưng không ai hiểu ta hãy đặt tên cho đúng chức năng .

{% highlight java  linenos %}
public class Example {
	public void deleteItems() {

	}
}
{% endhighlight %}

<br>
# **6. Đặt tên không gây hiểu lầm**

{% highlight java  linenos %}
public class Example1 {

	//Tên này không tốt vì nó là tên của các hệ thống và ứng dụng
	private String hp, aix, sco;chrome

	//Tên này không tốt vì từ list là những thứ liên quan đến lập trình như linkedlist, arraylist ///dể gây hiểu nhầm
	private List<String> accountList;

	//Đây là cách đặt tên tốt.
	private List<String> accountGroup,accounts,groupofAccount ;
}
{% endhighlight %}

<br>
# **7. Đặt tên method bắt buộc phải là động từ**

Tên method trong Class luôn luôn phải là động từ. Nếu method dài từ 2 từ trở lên thì mình áp dụng đặt tên theo phương phát camel (con lạc đà ) chữ đầu tiên viết thường chữ sau viết hoa.
Ví dụ phương  thức rút tiền withdrawMoney.

{% highlight java  linenos %}
public class Example1 {

  public void withdrawMoney(float money) {

  }

}
{% endhighlight %}

<br>
# **8. Đặt tên Class bắt buộc phải là danh từ**

Tên của một Class luôn luôn là danh từ. Nếu tên Class có 2 từ trở lên thì ta viết hoa hai chữ cái đầu tiên. Ví dụ CustomerRepository

{% highlight java  linenos %}
public class Customer {

}
{% endhighlight %}

<br>
# **9. Tránh đặt tên gây khó buộc người đọc phải đoán nó**

Lập trình viên đa số hay bị lỗi này. Thường để tiết kiệm thời gian , lập trình viên thường đặt tên biết bằng một ký tự . Ví dụ vòng lặp sau nó như một dòng code đánh đố người đọc để suy luận ra i , k là gì?

{% highlight java  linenos %}
public class Example1 {


	for (int i=0,i<size,i++) {
		if (i == k) {

		}
	}
}
{% endhighlight %}

<br>
# **10. Thêm bối cảnh để biến có ý nghĩa**

Ví dụ mình có các biến sau trong class Persion  với tên như sau: firstName, lastName, street, houseNumber, city, state và zipcode. Như vậy ta hiểu được các biến sau đang mô tả cho một địa chỉ của một người.

{% highlight java  linenos %}
public class Person {

  private String firstName;
  private String lastName;  
  private String street;
  private int houseNumber;
  private String city;
  private String state;
  private String zipcode;  

}
{% endhighlight %}

Ở ví dụ tiếp theo mình chú ý vào biến state mình không hiểu nó là đang nói về  địa chỉ hay không?


{% highlight java  linenos %}
public class Person {

  public void getMailbox() {
    String  zipcode = getZipCode();
    String state = zipcode.concat("");
  }


}
{% endhighlight %}

Như vậy để tăng thêm ý nghĩa cho từ state là nói về địa chỉ, ta thêm tiền tố addressState. Như vậy khi người dùng đọc vào biết là biến state đó đang nói về địa chỉ

<br>
# **Tóm tắt**

Trên đây là 10 cách đặt tên biết có ý nghĩa. Nếu chúng ta tuân thủ các bước này thì code của chúng ta sẽ sạch sẽ hơn. Người đọc dể hiểu hơn, từ đó dẫn đến việc duy trì ,phát triển sản phẩm dể dàng hơn.
