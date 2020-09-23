---
layout: course-design-pattern
title: Sử dụng Singletion Design Pattern
slug : singleton-design-pattern
category: craftmanship
tags: [designpattern]
summery: Singleton
image: /images/blog/design-patterns.png
description : Sử dụng Singleton design pattern trong lập trình java. Hướng dẫn sử dụng Singleton design pattern trong học lập trình java thông qua các ví dụ. Hiểu nguyên lý  khi nào sử dụng Singleton design pattern trong lập trình.
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em, chủ đề hôm nay của anh sẽ bàn về <b>Design Pattern</b> là <b>Singleton </b> ? Khi nào chúng ta sẽ dùng nó trong lập trình.

<br>
# **1- Singleton Là gì ?**

Singleton Pattern giúp chúng ta tạo ra một đối tượng duy nhất trong hệ thống. Ví dụ như anh muốn xây dựng đối tượng cache. Thì trong toàn bộ chương trình anh chỉ có một đối tượng đó chứa các giá trị. Các modules khác trong hệ thống có thể lấy giá trị này ra. Cho dù nhiều module cùng thao tác lấy giá trị từ cache , nhưng giá trị vẫn lấy ra và cập nhật đúng vì trong cả chương trình ta chỉ có 1 đối tượng cache duy nhất. Nó được dùng để chia sẽ với các modules mà gọi nó.

# **2- Khi nào nên dùng Singleton**

+ Khi chúng ta muốn có một đối tượng duy nhất xuyên suốt ứng dụng.

<br>
# **3- Singleton UML**

{:refdef: style="text-align: center;"}
![Abstract Factory UML ](/images/post/designpattern/singletonUML.png){:class="img-responsive"}
{: refdef}

<br>
# **4-Phương án 1 : Tạo Singleton không phải threadsafe**

- Để tạo được Singleton thì ta có các bước sau.

{% highlight java  %}
public final class Singleton {
    private static Singleton instance;
    public String value;

    private Singleton(String value) {
        try {
            Thread.sleep(1000);
        } catch (InterruptedException ex) {
            ex.printStackTrace();
        }
        this.value = value;
    }

    public static Singleton getInstance(String value) {
        if (instance == null) {
            instance = new Singleton(value);
        }
        return instance;
    }
}

{% endhighlight %}

- Bước 1 : Tạo một biến static của class :  private static Singleton instance
- Bước 2 : Khai báo constructor là private chứ không phải là public : private Singleton(String value)
- Bươc 3 : tạo method getInstance trả về đối tượng Singleton static Singleton getInstance(String value)

- Sử dụng Singleton bằng cách sau đây.

- Chúng ta tạo đối tượng thông qua phương thức getInstance : Singleton singleton = Singleton.getInstance("FOO");
- Sau đó chúng ta có thể lấy giá trị được chứa trong instance : singleton.value

{% highlight java  %}
public class DemoSingleThread {
    public static void main(String[] args) {
        System.out.println("If you see the same value, then singleton was reused (yay!)" + "\n" +
                "If you see different values, then 2 singletons were created (booo!!)" + "\n\n" +
                "RESULT:" + "\n");
        Singleton singleton = Singleton.getInstance("FOO");
        Singleton anotherSingleton = Singleton.getInstance("BAR");
        System.out.println(singleton.value);
        System.out.println(anotherSingleton.value);
    }
}

{% endhighlight %}

- Như vậy trong toàn bộ hệ thống của chúng ta chỉ có 1 đối tượng Singleton duy nhất và lấy nó ra bằng phương thức getInstance. Ngoài ra chúng ta có thể định nghĩa một loạt các method trong class Singleton như setValue(), getValue() hoặc bất cứ phương thức nào tuỳ thích.

- Có một vấn đề xảy ra ở Singleton ở trên là nếu như anh có nhiều Thread (tiến trình) cùng truy cập vào biến Singletion để lấy dữ liệu thì sẽ xảy ra xung đột. Để tránh tình trạng đó chúng ta sử dụng Threadsafe như sau

# **5-Phương án 2 : Tạo Singleton với threadsafe**

{% highlight java  %}
public final class Singleton {
    
    private static volatile Singleton instance;

    public String value;

    private Singleton(String value) {
        this.value = value;
    }

    public static Singleton getInstance(String value) {
        Singleton result = instance;
        if (result == null) {
            synchronized (Singleton.class) {
                result = instance;
                if (result == null) {
                    instance = result = new Singleton(value);
                }
            }
        }
        return instance;
    }
}
{% endhighlight %}

- Có một điều khác biệt trong phương thức getInstance là chúng ta thêm vào từ khoá đồng bộ synchronized khi tạo ra đối tượng Singleton. Như vậy khi có 2 hay nhiều tiến trình cùng yêu cầu tạo đối tượng thì nó sẽ chờ cho tiến trình trước đó xong xuôi rồi nó mới làm. Như vậy sẽ tránh tình trạnh xung đột khi nhiều tiến trình nhiều module cùng truy xuất tạo đối tượng cùng một lúc


{% highlight java  %}
public class DemoMultiThread {
    public static void main(String[] args) {
        System.out.println("If you see the same value, then singleton was reused (yay!)" + "\n" +
                "If you see different values, then 2 singletons were created (booo!!)" + "\n\n" +
                "RESULT:" + "\n");
        Thread threadFoo = new Thread(new ThreadFoo());
        Thread threadBar = new Thread(new ThreadBar());
        threadFoo.start();
        threadBar.start();
    }

    static class ThreadFoo implements Runnable {
        @Override
        public void run() {
            Singleton singleton = Singleton.getInstance("FOO");
            System.out.println(singleton.value);
        }
    }

    static class ThreadBar implements Runnable {
        @Override
        public void run() {
            Singleton singleton = Singleton.getInstance("BAR");
            System.out.println(singleton.value);
        }
    }
}

{% endhighlight %}