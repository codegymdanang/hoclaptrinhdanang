---
layout: course-design-pattern
title: Sử dụng Strategy trong lập trình java
slug : strategy-design-pattern
category: craftmanship
tags: [designpattern]
summery: Strategy pattern
image: /images/blog/design-patterns.png
description : Sử dụng Strategy trong lập trình java. Hướng dẫn sử dụng Strategy factory trong học lập trình java thông qua các ví dụ. Hiểu nguyên lý  khi nào sử dụng Strategy factory trong lập trình.
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em, chủ đề hôm nay của anh sẽ bàn về <b>Design Pattern</b> <b>Method Factory</b> ? Khi nào chúng ta sẽ dùng nó trong lập trình.

<br>
# **1- Strategy Pattern là gì ?**

Chúng ta dùng <b>Strategy Pattern</b> để quản lý thuật toán , các mối quan hệ giữa các object trong ứng dụng

# **2- Khi nào nên dùng Abstract Factory**

Chúng ta sử dụng <b>Strategy</b> khi chúng ta muốn chọn một thuật toán cho một đối tượng cụ thể lúc runtime (chương trình đang chạy). Ví dụ như thuật toán thanh toán cho khi mua hàng online trên mạng. Chúng ta có thể thanh toán bằng thẻ visa hay master. Thì khi chương trình mình dang chạy nếu người dùng chọn visa thì mình sẽ dùng thuật toán tính tiền của visa để thanh toán. Như vậy ta wrap các thuật toán , các business thành một đối tượng và sử dụng nó


# **3- Strategy UML**

{:refdef: style="text-align: center;"}
![Method Strategy ](/images/post/designpattern/strategyuml.png){:class="img-responsive"}
{: refdef}

Ví dụ sau dây ta làm cho thuật toán nén file. Người dùng có thể nén bằng zip hoặc bằng rar

{% highlight java  linenos %}

//Strategy Interface
public interface CompressionStrategy {
  public void compressFiles(ArrayList<File> files);
}
{% endhighlight %}

{% highlight java  linenos %}
public class ZipCompressionStrategy implements CompressionStrategy {
  public void compressFiles(ArrayList<File> files) {
    //using ZIP approach
  }
}
{% endhighlight %}

{% highlight java  linenos %}
public class RarCompressionStrategy implements CompressionStrategy {
  public void compressFiles(ArrayList<File> files) {
    //using RAR approach
  }
}
{% endhighlight %}

{% highlight java  linenos %}
public class CompressionContext {
  private CompressionStrategy strategy;
  //this can be set at runtime by the application preferences
  public void setCompressionStrategy(CompressionStrategy strategy) {
    this.strategy = strategy;
  }
  
  //use the strategy
  public void createArchive(ArrayList<File> files) {
    strategy.compressFiles(files);
  }
}
{% endhighlight %}

{% highlight java  linenos %}
public class Client {
  public static void main(String[] args) {
    CompressionContext ctx = new CompressionContext();
    //we could assume context is already set by preferences
    ctx.setCompressionStrategy(new ZipCompressionStrategy());
    //get a list of files...
    ctx.createArchive(fileList);
  }
}
{% endhighlight %}