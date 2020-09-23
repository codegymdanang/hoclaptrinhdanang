---
layout: course-java
title: Ngoại lệ trong ngôn ngữ lập trình
slug : ngoai-le
category: laptrinhjava
tags: [java core]
summery: Ngoại Lệ
image: /images/blog/java.png
featureImage: /images/post/javacore/feature_exception.png
description : Tìm hiểu ngoại lệ là gì trong ngôn ngữ lập trình java. Chúng ta sẽ tìm hiểu check exception và uncheck exception là gì. Cách sử dụng try catch finaly để bắt ngoại lệ trong ngôn ngữ lập trình và các phương pháp ném ngoại lệ trong ngôn ngữ java.

youtubeId: zC0t0e9DaH4
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn , hôm nay chủ đề của anh sẽ nói về <b>Ngoại lệ</b> (Exception) trong lập trình là gì ?

<br>
# **1. Ngoại lệ (Exception) là gì ?**

<b>Exception</b> (ngoại lệ) trong Java là một vấn đề bất thường xảy ra trong quá trình thực hiện của chương trình mà mình có thể dự đoán hoặc không dự đoán trước.

<b>Exception</b> là một sự kiện mà phá vỡ luồng chuẩn của chương trình. Anh lấy ví dụ về rút tiền ATM ở máy rút tiền. Trong tài khoản
mình chỉ có 1.000.000 nhưng nếu mình bấm trong máy ATM rút 2.000.000 thì lúc đó chương trình trong máy ATM sẽ báo lỗi vì
số tiền mình yêu cầu rút lớn hơn số hiện tại. Đó chính là một Exception (ngoại lệ) xảy ra lúc chương trình đang chạy.

Đối với lập trình viên mình phải bắt và xử lý các <b>ngoại lệ</b> trong chương trình. Nếu không chương trình sẽ bị dừng. Thường các
lập trình viên có thể bắt lại <b>Expection</b> trong lúc viết code hoặc dự đoán được Exception trong lúc chương trình đang chạy
để từ đó lập trình viên có thể xử lý các ngoại lệ đó mà chương trình vẫn tiếp tục chạy.

<br>
# **2. Check Exception**

- Những lỗi developer có thể đoán trước được.
- Bắt buộc developer phải bắt và xử lý <b>ngoại lệ</b> trong lúc compile time (lúc đang code).

Ví dụ các lỗi mà trong lúc code lập trình viên có thể đoán được.

- FileNotFoundException.
- InterruptException.
- Database Exception.
- IO Exception.

<br>
# **3. Uncheck Exception**

- Những lỗi xảy ra khi chương trình đang chạy và chúng ta không biết chắc nó có xảy ra hay không.
- Không yêu cầu developer phải bắt và xử lý ngoại lệ trong lúc compile time (lúc đang code). Nhưng mà
phải dự đoán được có khả năng xảy ra lỗi ở những đoạn code nào từ đó bắt lỗi cho đoạn code đó.

Ví dụ : Khi anh viết một chương trình cho nhà bank với chức năng rút tiền.
Sẽ có những trường hợp lỗi xảy ra khi chương trình đang chạy đó là việc khách hàng có thể rút tiền nhiều hơn số tiền họ hiện có trong tài khoản.
Lúc này mình phải dự đoán cái hàm viết phương thức rút tiền có khả năng xảy ra lỗi và mình sẽ viết code  để xử lý ngoại lệ đó .

<br>
# **4. Kiến trúc của ngoại lệ**

{:refdef: style="text-align: center;"}
![Exception ](/images/post/javacore/exception.png){:class="img-responsive"}
{: refdef}

- Throwable : là cha của tất cả <b>ngoại lệ</b> xảy ra trong chương trình bao gồm lỗi (<b>Error</b>) và ngoại lệ (<b>Exception</b>).

- Error : là tất cả những lỗi được bắt từ JMV (Máy ảo Java). Ví dụ như Error OutOfMemory hoặc chia một số cho 0.Các em có thể tìm hiểu thêm về bộ nhớ của chương trình tại [đây](https://levunguyen.com/laptrinhjava/2020/04/07/phan-biet-bo-nho-heap-va-stack/) .

- Excepton : là cha của tất cả class Check Exception. Mình khai báo một Class và kế thừa Class Exception.
{% highlight java linenos %}
public class MyDepositException extends Exception {

	public MyBusinessException(String message, Throwable cause, ErrorCode code) {
		super(message, cause);
		this.code = code;
	}
}
{% endhighlight %}

Anh sử dụng <b>ngoại lệ</b> MyDepositException như sau.

{% highlight java linenos %}
private void wrapException(String input) throws MyDepositException {
	try {
		// do something
	} catch (NumberFormatException e) {
		throw new MyDepositException("Rut tien vuot dinh muc", e, 5004);
	}
}
{% endhighlight %}

- <b>Exception Runtime</b> : là cha của tất cả các class Uncheck. Anh khai báo một Class và kế thừa RuntimeExcepton. Những lỗi này thường xảy ra khi chương trình đang chạy.

{% highlight java linenos %}
public class MyDepositRuntimeException extends RuntimeException {


	private final ErrorCode code;

	public MyDepositRuntimeException(ErrorCode code) {
		super();
		this.code = code;
	}

	public MyDepositRuntimeException(String message, Throwable cause, ErrorCode code) {
		super(message, cause);
		this.code = code;
	}

	public MyDepositRuntimeException(String message, ErrorCode code) {
		super(message);
		this.code = code;
	}

	public MyDepositRuntimeException(Throwable cause, ErrorCode code) {
		super(cause);
		this.code = code;
	}

	public ErrorCode getCode() {
		return this.code;
	}
}
{% endhighlight %}

Mình sử dụng MyDepositRuntimeException như sau.

{% highlight java linenos %}
private void wrapException(String input) {
	try {
		// do something
	} catch (NumberFormatException e) {
		throw new MyDepositRuntimeException("Loi rut tien", e, 5005);
	}
}
{% endhighlight %}
<br>
# **5. Ném ngoại lệ bằng Throws hoặc throw**

- Trong các ngôn ngữ lập trình khi một <b>ngoại lệ</b> xảy ra ,mình dùng từ khoá **throw** hoặc **throws** để ném ngoại lệ đó ra.

- Trong Java mình có thể dùng từ khoá throws bên cạnh tên method để ném ngoại lệ. Ví dụ như public void deposit(int depositAmount) throws Exception . Phương thức nào
mà gọi method deposit phải bắt lại ngoại lệ và xử lý . Để bắt ngoại lệ thì mình dùng khối  **try**, **catch** , **finally** lệnh để bắt ngoại lệ bắt từ hàm deposit ném ra

- Ngoài cách dùng <b>Throws</b> ta có thể dùng <b>throw new Exception</b>  bên trong method như ví dụ dưới  đây .

{% highlight java linenos %}
/**
 * @exception FileNotFoundException ...
 */
public Scanner(String fileName) throws FileNotFoundException {
   // ...
}

public void deposit(int depositAmount) throws Exception {
   if (depositAmount > getAmount()) {
       throw new Exception("Current Amount is less than Deposit");
   }
   System.out.println("Deposit is valid " + depositAmount);
}
{% endhighlight %}

<br>
# **6. Bắt ngoại lệ bằng try catch**

Chúng ta sử dụng từ khoá <b>try</b>, <b>catch</b> để bắt ngoại lệ và xử lý. Nếu chúng ta không bắt ngoại lệ lại và sử lý thì chương trình có nguy cơ bị đứng. Hoặc nghiêm trọng hơn là ứng dụng bị chết và không chạy được. Nhờ sử dụng try catch mà ta có thể sử lý ngoại lệ giúp chương trình tiếp tục chạy.

{% highlight java linenos %}
public int getPlayerScore(String playerFile) {
    try {
        Scanner contents = new Scanner(new File(playerFile));
        return Integer.parseInt(contents.nextLine());
    } catch (FileNotFoundException noFile) {
        throw new IllegalArgumentException("File not found");
    }
}
{% endhighlight %}

<br>
# **7. Bắt ngoại lệ bằng nhiều catch**

Khi gọi một method, nhưng nếu method đó ném ra nhiều hơn 1 ngoại lệ. Ta có thể sử dụng nhiều <b>catch</b> để bắt các ngoại lệ đó. Mỗi catch sẽ bắt một ngoại lệ tương ứng.

{% highlight java linenos %}
public int getPlayerScore(String playerFile) {
    try (Scanner contents = new Scanner(new File(playerFile))) {
        return Integer.parseInt(contents.nextLine());
    } catch (IOException e) {
        logger.warn("Player file wouldn't load!", e);
        return 0;
    } catch (NumberFormatException e) {
        logger.warn("Player file was corrupted!", e);
        return 0;
    }
}
{% endhighlight %}

<br>
# **8. Khối lệnh Finally**

Các đoạn code trong khối lệnh <b>Finally</b> luôn luôn chạy cho dù có xảy ra lỗi ở trong khối lệnh try hay catch . Khối lệnh Finally thường dùng để.

- Đóng kết nối xuống file .
- Đóng kết nối xuống database.
- Giải phóng bộ nhớ. Để hiểu thêm về bộ nhớ bạn có thể đọc bài viết tại [đây](https://levunguyen.com/laptrinhjava/2020/04/07/phan-biet-bo-nho-heap-va-stack/)

<br>
# **9. Video demo tạo Exception trong Java**

{:refdef: style="text-align: center;"}
{% include youtubePlayer.html id=page.youtubeId %}
{: refdef}
