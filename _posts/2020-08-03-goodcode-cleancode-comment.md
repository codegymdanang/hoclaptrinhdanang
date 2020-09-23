---
layout: course-goodcode
title: Clean Code Về Comment
slug : clean-code-comment
category: craftmanship
tags: [goodcode]
summery: Comment
image: /images/blog/quality-code.png
description : Clean Code Comment trong lập trình lập trình. Hiều clean code là gì, hướng dẫn cách sử dụng method đúng trong học lập trình.
youtubeId: aSDKxAUqcTc
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em, hôm nay anh sẽ trình bày chủ đề về viết comment như thế nào là hiệu quả.

# **1. Noise Comment**

Noise comment là những comment mà lập trình viên mình ghi chú nhưng gây khó chịu cho người đọc. Không cung cấp thông tin cần thiết cho người đọc.

- Code không tốt

{% highlight java  linenos %}

public class Noise {

	
	/**
	* Default constructor.
	*/
	protected AnnualDateRule() {
	}
	No, really? Or how about this:
	/** The day of the month. */
	private int dayOfMonth;
	And then there’s this paragon of redundancy:
	/**
	* Returns the day of the month.
	*
	* @return the day of the month.
	*/
	public int getDayOfMonth() {
	return dayOfMonth;
	}
}

{% endhighlight %}


<br>
# **2. Mumbling Comment**

Nhiều lúc mình thích ghi những comment mà mình nghĩ mình nên làm hoặc bởi vì chương trình cần. Ví dụ dưới đây trong hàm catch ngoại lệ. Nếu rơi vào trường hợp ngoại lệ thì sẽ nạp các giá trị từ file mặc định. Nhưng người viết lại không nói rõ là load ở đâu, cái gì sẽ load những giá trị mặc định này. Nếu khác đọc vào thì rất khó hiểu thay vì comment như vậy mình nên viết các chức năng khi xảy ra lỗi.

- Code không tốt

{% highlight java  linenos %}

public class Mumbling {


	public void loadProperties() {
		try {
			String propertiesPath = propertiesLocation + "/" + PROPERTIES_FILE;
			FileInputStream propertiesStream = new FileInputStream(propertiesPath);
			loadedProperties.load(propertiesStream);
		} catch (IOException e) {
			// No properties files means all defaults are loaded
		}
	}
}


{% endhighlight %}

<br>
# **3. Journal Comment**

Mình viết comment trên cái file mô tả từng ngày mình chỉnh sửa cái file, giống như mô tả một cuộc hành trình. Hiện nay các source code như github, gitlab hoặc bitbucket đều có khả năng xem lại history của sự thay đổi mình không nên làm giống cách dưới đây.

- Code không tốt

{% highlight java  linenos %}

public class Journal {
	
	* Changes (from 11-Oct-2001)
	* --------------------------
	* 11-Oct-2001 : Re-organised the class and moved it to new package
	* com.jrefinery.date (DG);
	* 05-Nov-2001 : Added a getDescription() method, and eliminated NotableDate
	* class (DG);
	* 12-Nov-2001 : IBD requires setDescription() method, now that NotableDate
	* class is gone (DG); Changed getPreviousDayOfWeek(),
	* getFollowingDayOfWeek() and getNearestDayOfWeek() to correct
	* bugs (DG);
	* 05-Dec-2001 : Fixed bug in SpreadsheetDate class (DG);
	* 29-May-2002 : Moved the month constants into a separate interface
	* (MonthConstants) (DG);
	* 27-Aug-2002 : Fixed bug in addMonths() method, thanks to N???levka Petr (DG);
	* 03-Oct-2002 : Fixed errors reported by Checkstyle (DG);
	* 13-Mar-2003 : Implemented Serializable (DG);
	* 29-May-2003 : Fixed bug in addMonths method (DG);
	* 04-Sep-2003 : Implemented Comparable. Updated the isInRange javadocs (DG);
	* 05-Jan-2005 : Fixed bug in addYears() method (1096282) (DG);
	
	/*Long ago there was a good reason to create and maintain these log entries at the start
	of every module. We didn’t have source code control systems that did it for us. Nowadays,
	however, these long journals are just more clutter to obfuscate the module. They should be
	completely removed.*/

}

{% endhighlight %}

<br>
# **4. Comment các code không dùng**

Trong code chúng ta nhiều khi không sử dụng như lại không xoá đi mà chúng ta comment lại. Hiện nay cách source control đều có thể giữ các code chúng ta trên đấy và chúng ta có thể revert lại version củ bất cứ khi nào chúng ta muốn. Nên không cần phải comment lại code mà không dùng. Tốt nhất nên xoá đi.

- Code không tốt

{% highlight java  linenos %}

public class Journal {
	
public class CommentOutCode {

	/*There was a time, back in the sixties, when commenting-out code might have been
	useful. But we’ve had good source code control systems for a very long time now. Those
	systems will remember the code for us. We don’t have to comment it out any more. Just
	delete the code. We won’t lose it. Promise*/
	
	
	InputStreamResponse response = new InputStreamResponse();
	response.setBody(formatter.getResultStream(), formatter.getByteCount());
	// InputStream resultsStream = formatter.getResultStream();
	// StreamReader reader = new StreamReader(resultsStream);
	// response.setContent(reader.read(formatter.getByteCount()));
}

}

{% endhighlight %}

<br>
# **5. Đặt comment ở thẻ dóng**

Thỉnh thoảng chúng ta hay thấy các lập trình viên thường ghi chú comment ở các thẻ đóng. Ví dụ dưới đây như khi kết thúc vòng while thì hay dùng comment //while để chú thích là hết vòng while.

- Code không tốt

{% highlight java  linenos %}

public class ClosingBrace {

	public static void main(String[] args) {
		BufferedReader in = new BufferedReader(new InputStreamReader(System.in));
		String line;
		int lineCount = 0;
		int charCount = 0;
		int wordCount = 0;
		try {
			while ((line = in.readLine()) != null) {
				lineCount++;
				charCount += line.length();
				String words[] = line.split("\\W");
				wordCount += words.length;
			} // while
			System.out.println("wordCount = " + wordCount);
			System.out.println("lineCount = " + lineCount);
			System.out.println("charCount = " + charCount);
		} // try
		catch (IOException e) {
			System.err.println("Error:" + e.getMessage());
		} // catch
	} // main

}

{% endhighlight %}

<br>
# **Tuy nhiên vẫn có một số comment là có lợi và nên dùng**

<br>
# **1. Comment mang tính phóng đại**

Khi mình muốn nhấn mạnh sự quan trọng của một dòng code. Nếu không dùng nó có thể ảnh đến hệ thống. Lúc này mình nên comment cho các lập trình viên khác biết để họ không xoá hoặc làm sai.

- Code tốt

{% highlight java  linenos %}

public class Amplification {

	//A comment may be used to amplify(phong dai   ) the importance of something that may otherwise seem inconsequential
	
	
	
	String listItemContent = match.group(3).trim();
	// the trim is real important. It removes the starting // spaces that could cause the item to be recognized
	// as another list.
	new ListItemWidget(this, listItemContent, this.level + 1); return buildList(text.substring(match.end()));

}
{% endhighlight %}

<br>
# **2. Comment mang tính giải thích**

Như đoạn code dưới đây mình giải thích a == a là dùng làm gì. 

- Code tốt

{% highlight java  linenos %}

public class Clarification {

	//Sometimes it is just helpful to translate the meaning of some obscure argument 
	//or return value into something that’s readable
	
	public void testCompareTo() throws Exception {
		WikiPagePath a = PathParser.parse("PageA"); 
		WikiPagePath ab = PathParser.parse("PageA.PageB"); 
		WikiPagePath b = PathParser.parse("PageB"); 
		WikiPagePath aa = PathParser.parse("PageA.PageA"); 
		WikiPagePath bb = PathParser.parse("PageB.PageB"); 
		WikiPagePath ba = PathParser.parse("PageB.PageA");
		}
		assertTrue(a.compareTo(a) == 0);  // a == a
		assertTrue(a.compareTo(b) != 0);   // a != b 
		assertTrue(ab.compareTo(ab) == 0); // ab == ab
		assertTrue(a.compareTo(b) == -1);  // a < b 
		assertTrue(aa.compareTo(ab) == -1); // aa < ab 
		assertTrue(ba.compareTo(bb) == -1); // ba < bb
		assertTrue(b.compareTo(a) == 1);  // b > a
		assertTrue(ab.compareTo(aa) == 1); // ab > aa
		assertTrue(bb.compareTo(ba) == 1);  // bb > ba
		
		
			
}
{% endhighlight %}

<br>
# **3. Comment mang tính giải thích dự định mình làm gì**

Comment lại những giải thích của mình cho chức năng mình đang làm. Có thể khi đọc code người khác mình không đồng ý cách mình đang viết nhưng ít nhất họ hiểu mình đang làm cái gì

- Code tốt

{% highlight java  linenos %}
public class ExplanationOfIntent {
	
	//Here’s an even better example. You might not agree with the programmer’s solution to the problem, 
	//but at least you know what he was trying to do.

	public void testConcurrentAddWidgets() throws Exception { 
		WidgetBuilder widgetBuilder = new WidgetBuilder(new Class[]{BoldWidget.class});
		String text = "'''bold text'''"; ParentWidget parent =
				new BoldWidget(new MockWidgetRoot(), "'''bold text'''"); AtomicBoolean failFlag = new AtomicBoolean(); failFlag.set(false);
				//This is our best attempt to get a race condition 
				//by creating large number of threads.
				for (int i = 0; i < 25000; i++) {
					WidgetBuilderThread widgetBuilderThread =
					new WidgetBuilderThread(widgetBuilder, text, parent, failFlag);
					Thread thread = new Thread(widgetBuilderThread);
					thread.start(); 
				}
				assertEquals(false, failFlag.get());
	}
	
}
{% endhighlight %}

<br>
# **5. Comment thông tin đơn giản ngắn gọn**

Nhiều lúc chúng ta nên cung cấp những thông tin cơ bản nhất trong comment để người đọc có thể hình dung được.

- Code tốt

{% highlight java  linenos %}

//It is sometimes useful to provide basic information with a comment. 
	//For example, con- sider this comment that explains the return value of an abstract method:
	
	// Returns an instance of the Responder being tested.
	protected abstract Responder responderInstance();
	
	// format matched kk:mm:ss EEE, MMM dd, yyyy 
	Pattern timeMatcher = Pattern.compile("\\d*:\\d*:\\d* \\w*, \\w* \\d*, \\d*");
	
}
{% endhighlight %}

<br>
# **6. Comment bản quyền của mình vào các dòng code**

- Code tốt

{% highlight java  linenos %}
public class Legal {
	
	//Sometimes our corporate coding standards force us to write certain comments for legal reasons. 
	//For example, copyright and authorship statements are necessary and reasonable things 
	//to put into a comment at the start of each source file.

	/ Copyright (C) 2003,2004,2005 by Object Mentor, Inc. All rights reserved.
	// Released under the terms of the GNU General Public License version 2 or later.
}
{% endhighlight %}

<br>
# **7. Comment những dòng code quan trọng**

Thỉnh thoảng chúng ta chú thích những đoạn code những dòng biến on off quan trọng, nếu sửa sai sẽ gây ra những hậu quả nghiêm trọng . Điều đó sẽ giúp các developer khác thận trọng khi muốn chỉnh sửa code.

- Code tốt

{% highlight java  linenos %}
public class WarningOfConsequences {

	//Sometimes it is useful to warn other pro- grammers about certain consequences. 
	//For example, here is a comment that explains why a particular test case is turned off:
	// Don't run unless you
	// have some time to kill.
	public void _testWithReallyBigFile() {
		writeLinesToFile(10000000);
		response.setBody(testFile);
		response.readyToSend(this);
		String responseString = output.toString(); assertSubString("Content-Length: 1000000000", responseString); assertTrue(bytesSent > 1000000000);
	}

}
{% endhighlight %}


# **Tóm tắt**

Comment có những cái tốt và những cái không tốt. Do vậy khi lập trình mình nên ghi càng rõ càng tốt. Viết code sao mà không cần sử dụng comment thì người khác đọc vẫn hiểu ý định của mình.
