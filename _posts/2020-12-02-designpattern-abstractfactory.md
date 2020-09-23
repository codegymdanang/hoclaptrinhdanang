---
layout: course-design-pattern
title: Sử dụng Abstract Factory trong lập trình java
slug : abstract-factory-design-pattern
category: craftmanship
tags: [designpattern]
summery: Abstract Factory
image: /images/blog/design-patterns.png
description : Sử dụng Abstract Factory trong lập trình java. Hướng dẫn sử dụng abstract factory trong học lập trình java thông qua các ví dụ. Hiểu nguyên lý  khi nào sử dụng abstract factory trong lập trình.
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em, chủ đề hôm nay của anh sẽ bàn về <b>Design Pattern</b> <b>Abstract Factory</b> ? Khi nào chúng ta sẽ dùng nó trong lập trình.

<br>
# **1- Abstract Factory Là gì ?**

# **2- Khi nào nên dùng Abstract Factory**
+ Khi chúng ta muốn tạo một họ sản phẩm (FAMILY PRODUCT) liên quan đến . Ví dụ như mình muốn tạo một đối tượng là Xe hơi Toyota. Thì các thành phần cấu thành xe hơi Toyota phải từ chính Toyota mà ra . Ví dụ Xe hơi Toyota thì Tay laí Toyota , lốp xe Toyota. Khung xe được sản xuất tại Toyota. Nói tóm lại các thành phần cấu tạo nên chiếc xe phải từ Toyota mà ra cả.

<br>
# **3- Abstract Factory UML**

{:refdef: style="text-align: center;"}
![Abstract Factory UML ](/images/post/designpattern/abstractfactoryUML.png){:class="img-responsive"}
{: refdef}

<br>
# **4- Abstract Factory Button và Checkbox**

{:refdef: style="text-align: center;"}
![Abstract Factory ](/images/post/designpattern/abstractfactory.png){:class="img-responsive"}
{: refdef}

<br>
# **5- Xây dựng ứng dụng**

Trong ví dụ  trên về xây dựng một ứng dụng Paint(vẽ) gồm có các phần như tạo button (nút) và tạo checkbox. Ứng với hệ điều hành Windows thì nó sẽ tạo ra bộ sản phẩm nút và check box của Windows. Nếu là hệ điều hành Mac thì nó sẽ tạo ra một bộ sản phẩm checkbox và nút bấm cho Mac. Như vậy phụ thuộc vào hệ điều hành mà mình đang dùng thì mình sẽ tạo các các thành phần tương ứng cho hệ điều hành đó. Không có trường hợp hệ điều hành Windows mà mình có thể tạo ra nút bấm Windows và Checkbox của Mac được.

1. GUI Factory trong thiết kế tương ứng với Abstract Facetory . Gui Factory gồm các method để tạo ra một sản phẩm . Mỗi method là tạo ra một phần của sản phẩm như button hay checkbox
2. MacOSFactory chính là ConcreatFactory1 : gồm các phương thức abstract để tạo ra button và checkbox tương ứng với Mac
3. WinOSFactory chính là ConcreatFactory 2 : gồm các phương thức abstract để tạo ra button và checkbox tương ứng với
4. Interface Button : Chính là AbstractProductA . Gồm phương thức vẽ để mô tả cho hành động vẽ button  là vẽ như thế nào  với mỗi hệ điều hành Windows hay Mac
5. Interface Checkbox : Chính là AbstractProductB . Gồm phương thức vẽ để mô tả cho hành động vẽ checkbox  là vẽ như thế nào với mỗi hệ điều hành Windows hay Mac
6. Windows Button : là ProductA2 . Đây là lớp định nghĩa Windows button là gì
7. Mac Button      : là ProductA1 . Đây là lớp định nghĩa Mac button là gì
8. Windows Checkbox : là ProductB2 . Đây là lớp định nghĩa Windows checkbox  là gì
9. Mac Checkbox     : là Product B1 . Đây là lớp định nghĩa Mac checkbox  là gì
10. Application : Sử dụng Gui Factory và 2 lớp Interface Button và Interface Checkbox để tạo ra họ sản phẩm . Nếu windows thì button và checkbox Windows và ngược lại

{% highlight java  linenos %}
public class Demo {

    /**
     * Application picks the factory type and creates it in run time (usually at
     * initialization stage), depending on the configuration or environment
     * variables.
     */
    private static Application configureApplication() {
        Application app;
        GUIFactory factory;
        String osName = System.getProperty("os.name").toLowerCase();
        if (osName.contains("mac")) {
            factory = new MacOSFactory();
            app = new Application(factory);
        } else {
            factory = new WindowsFactory();
            app = new Application(factory);
        }
        return app;
    }

    public static void main(String[] args) {
        Application app = configureApplication();
        app.paint();
    }
}
{% endhighlight %}

{% highlight java  linenos %}

/**
 * Factory users don't care which concrete factory they use since they work with
 * factories and products through abstract interfaces.
 */
public class Application {
    private Button button;
    private Checkbox checkbox;

    public Application(GUIFactory factory) {
        button = factory.createButton();
        checkbox = factory.createCheckbox();
    }

    public void paint() {
        button.paint();
        checkbox.paint();
    }
}
{% endhighlight %}

{% highlight java  linenos %}
/**
 * Abstract factory knows about all (abstract) product types.
 */
public interface GUIFactory {
    Button createButton();
    Checkbox createCheckbox();
}
{% endhighlight %}


{% highlight java  linenos %}
/**
 * Each concrete factory extends basic factory and responsible for creating
 * products of a single variety.
 */
public class MacOSFactory implements GUIFactory {

    @Override
    public Button createButton() {
        return new MacOSButton();
    }

    @Override
    public Checkbox createCheckbox() {
        return new MacOSCheckbox();
    }
}
{% endhighlight %}

{% highlight java  linenos %}
/**
 * Each concrete factory extends basic factory and responsible for creating
 * products of a single variety.
 */
public class WindowsFactory implements GUIFactory {

    @Override
    public Button createButton() {
        return new WindowsButton();
    }

    @Override
    public Checkbox createCheckbox() {
        return new WindowsCheckbox();
    }
}
{% endhighlight %}

{% highlight java  linenos %}
/**
 * Checkboxes is the second product family. It has the same variants as buttons.
 */
public interface Checkbox {
    void paint();
}

{% endhighlight %}

{% highlight java  linenos %}
/**
 * All products families have the same varieties (MacOS/Windows).
 *
 * This is a variant of a checkbox.
 */
public class MacOSCheckbox implements Checkbox {

    @Override
    public void paint() {
        System.out.println("You have created MacOSCheckbox.");
    }
}

{% endhighlight %}

{% highlight java  linenos %}
/**
 * All products families have the same varieties (MacOS/Windows).
 *
 * This is another variant of a checkbox.
 */
public class WindowsCheckbox implements Checkbox {

    @Override
    public void paint() {
        System.out.println("You have created WindowsCheckbox.");
    }
}
{% endhighlight %}

{% highlight java  linenos %}
/**
 * Abstract Factory assumes that you have several families of products,
 * structured into separate class hierarchies (Button/Checkbox). All products of
 * the same family have the common interface.
 *
 * This is the common interface for buttons family.
 */
public interface Button {
    void paint();
}
{% endhighlight %}

{% highlight java  linenos %}
/**
 * All products families have the same varieties (MacOS/Windows).
 *
 * This is a MacOS variant of a button.
 */
public class MacOSButton implements Button {

    @Override
    public void paint() {
        System.out.println("You have created MacOSButton.");
    }
}
{% endhighlight %}

{% highlight java  linenos %}
/**
 * All products families have the same varieties (MacOS/Windows).
 *
 * This is another variant of a button.
 */
public class WindowsButton implements Button {

    @Override
    public void paint() {
        System.out.println("You have created WindowsButton.");
    }
}

{% endhighlight %}

{% highlight java  linenos %}
public class Demo {

    /**
     * Application picks the factory type and creates it in run time (usually at
     * initialization stage), depending on the configuration or environment
     * variables.
     */
    private static Application configureApplication() {
        Application app;
        GUIFactory factory;
        String osName = System.getProperty("os.name").toLowerCase();
        if (osName.contains("mac")) {
            factory = new MacOSFactory();
            app = new Application(factory);
        } else {
            factory = new WindowsFactory();
            app = new Application(factory);
        }
        return app;
    }

    public static void main(String[] args) {
        Application app = configureApplication();
        app.paint();
    }
}
{% endhighlight %}
