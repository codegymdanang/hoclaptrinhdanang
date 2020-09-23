---
layout: course-design-pattern
title: Sử dụng Factory Method trong lập trình java
slug : factory-method-design-pattern
category: craftmanship
tags: [designpattern]
summery: Factory Method
image: /images/blog/design-patterns.png
description : Sử dụng  Factory Method trong lập trình java. Hướng dẫn sử dụng  Factory Method trong học lập trình java thông qua các ví dụ. Hiểu nguyên lý  khi nào sử dụng  Factory Method trong lập trình.
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em, chủ đề hôm nay của anh sẽ bàn về <b>Design Pattern</b> <b>Method Factory</b> ? Khi nào chúng ta sẽ dùng nó trong lập trình.

<br>
# **1- Factory method là gì ?**

<b>Factory Method</b> cho phép chúng ta tạo ra một đối tượng mà chúng ta không cần quan tâm nó được tạo ra như thế nào

# **2- Khi nào nên dùng Abstract Factory**

- Khi ta muốn tạo ra đối tượng lúc chương trình đang chay (run time) mà ta chưa biết nó sẽ trả về đối tượng gì.
- Khi các đối tượng được tạo ra có chung đặc điểm của lớp cha.
- Che dấu đối tượng được tạo ra . Client chỉ dùng nhưng không quan tâm các đối tượng con sẽ tạo ra như thế nào.



# **3- Method Factory UML**

{:refdef: style="text-align: center;"}
![Method Factory UML ](/images/post/designpattern/methodfactoryuml.gif){:class="img-responsive"}
{: refdef}

- Trong ví dụ sau chúng ta sẽ sử dụng Factory Method createButton để ra các dialog(Hộp thoại) trên hộp thoại đó sẽ có các button(nút bấm) khác nhau dự vào cái máy đang chạy ứng dụng này.

- Nếu máy Windows chạy chương trình này thì nó sẽ tạo ra hộp thoại và có nút theo định dạng của máy Windows.

- Nếu máy chạy chương trình này là Mac hay Ubuntu thì chúng ta sẽ tạo ra dialog có nút bấm tương ứng theo định dạng nút Mac hay Ubuntu

- Ví dụ máy của mình đang là máy Mac thì khi chạy chương trình nó sẽ sinh ra Dialog (hội thoại) có button (nút bấm) theo định dạng Mac. Ví dụ máy khác đang sử dụng là Windows thì khi chạy chương trình nó sẽ sinh ra Dialog (hội thoại) có button (nút bấm) theo định dạng Windows

# **4- Factory Method tạo ra Dialog (hộp thoại) với các button (nút bấm) khác nhau**

{:refdef: style="text-align: center;"}
![Method Factory  ](/images/post/designpattern/factorymethod.png){:class="img-responsive"}
{: refdef}

- Theo thiết kế ở trên thì HTML Button và Windows Button chính là 2 Concreat Class. Là 2 class sản phẩm được tạo ra từ abstract method createButton của HTML Dialog và Windows Dialog

- Abstract Dialog chính là Creator chứa method abstract và 1 phương thức để gọi Abstract

- HTML Dialog và Windows Dialog chính là 2 Concreat Creator . 2 class này sẽ kế thừa phương thức abstract class của lớp Abstract Dialog. 2 Class HTML Dialog và Windows Dialog kế thừa phương thức abstract createButton. Nhưng mỗi lớp sẽ cài đặt phương thức tạo ra button khác nhau. Kết quả của phương thức abstract sẽ sinh ra 1 đối tượng tương ứng. Ví dụ HTML Dialog thì sẽ tạo ra đối tượng HTML Button , còn Windows Dialog sẽ tạo ra Windows Button .

- Demo Application sẽ sử dụng Dialog để tuỳ vào hệ điều hành mà cho ra các sản phẩm dialog tương ứng (Win, Mac, Ubuntu). Demo Application chỉ dùng Abstract Dialog và không quan tâm các nút bấm được tạo ra như thế nào. Demo Application chỉ cần gọi dialog.renderWindow() để tạo ra hộp thoại với nút bấm tương ứng với hệ điều hành

{% highlight java  linenos %}

public class Demo {
    private static Dialog dialog;

    public static void main(String[] args) {
        configure();
        runBusinessLogic();
    }

    /**
     * The concrete factory is usually chosen depending on configuration or
     * environment options.
     */
    static void configure() {
        if (System.getProperty("os.name").equals("Windows 10")) {
            dialog = new WindowsDialog();
        } else {
            dialog = new HtmlDialog();
        }
    }

    /**
     * All of the client code should work with factories and products through
     * abstract interfaces. This way it does not care which factory it works
     * with and what kind of product it returns.
     */
    static void runBusinessLogic() {
        dialog.renderWindow();
    }
}
{% endhighlight %}


{% highlight java  linenos %}

public abstract class Dialog {

    public void renderWindow() {
        // ... other code ...

        Button okButton = createButton();
        okButton.render();
    }

    /**
     * Subclasses will override this method in order to create specific button
     * objects.
     */
    public abstract Button createButton();
}
{% endhighlight %}

{% highlight java  linenos %}

/**
 * Common interface for all buttons.
 */
public interface Button {
    void render();
    void onClick();
}

{% endhighlight %}


{% highlight java  linenos %}

/**
 * HTML button implementation.
 */
public class HtmlButton implements Button {

    public void render() {
        System.out.println("<button>Test Button</button>");
        onClick();
    }

    public void onClick() {
        System.out.println("Click! Button says - 'Hello World!'");
    }
}

{% endhighlight %}

{% highlight java  linenos %}

/**
 * Windows button implementation.
 */
public class WindowsButton implements Button {
    JPanel panel = new JPanel();
    JFrame frame = new JFrame();
    JButton button;

    public void render() {
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        JLabel label = new JLabel("Hello World!");
        label.setOpaque(true);
        label.setBackground(new Color(235, 233, 126));
        label.setFont(new Font("Dialog", Font.BOLD, 44));
        label.setHorizontalAlignment(SwingConstants.CENTER);
        panel.setLayout(new FlowLayout(FlowLayout.CENTER));
        frame.getContentPane().add(panel);
        panel.add(label);
        onClick();
        panel.add(button);

        frame.setSize(320, 200);
        frame.setVisible(true);
        onClick();
    }

    public void onClick() {
        button = new JButton("Exit");
        button.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                frame.setVisible(false);
                System.exit(0);
            }
        });
    }
}

{% endhighlight %}