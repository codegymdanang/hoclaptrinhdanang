---
layout: course-css
title: Sử dụng đơn vị do trong CSS  
slug : don-vi-do-css
category: laptrinhweb
tags: [css]
summery: Đơn vi đo  
image: /images/blog/angular.png
description : Sử dụng đơn vi đo trong trong dự án làm web. Hướng dẫn Sử dụng đơn vi đo trong CSS vào dự án web. 
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người cách sử dụng <b>đơn vi đo</b> là như thế nào?

# **1. Đơn vị do**

Trong css hỗ trợ cho chúng ta các đơn vị đo như inches, centimeters, phần trăm , em hoặc point 

- Ví dụ như ta muốn border của một table có kích thướt là 1px thì ta khai báo như sau.

{% highlight html linenos %}

   table { border :1px solid #C00; }

{% endhighlight %}

# **2. Đơn vị do phần trăm**

Ví dụ anh mong muốn các chữ trong đoạn văn bản có chiều cao là 125% thì anh khai báo như sau

{% highlight html linenos %}

  p {font-size: 16pt; line-height: 125%;}

{% endhighlight %}

# **3. Đơn vị do centimeters**

Ví dụ như anh mong muốn khoảng cách khối lệnh div  là 2 cm thì anh khai báo như sau

{% highlight html linenos %}

div { margin-bottom: 2cm;}

{% endhighlight %}

# **4. Đơn vị do em**

Ví dụ anh mong muốn khoảng cách giữa các ký tự trong đoạn văn là 7em.

{% highlight html linenos %}

p {letter-spacing: 7em;}

{% endhighlight %}

# **5. Đơn vị do ex**

Ví dụ anh muốn kích thước của fornt chữ cho chiều cao trong một đoạn văn bản

{% highlight html linenos %}

p {font-size: 24pt; line-height: 3ex;}

{% endhighlight %}

# **6. Đơn vị do in**

Ví dụ anh muốn khoảng cách giữa các từ trong một văn bản cách nhau 15 inches


{% highlight html linenos %}

p {word-spacing: .15in;}

{% endhighlight %}

# **7. Đơn vị do milimeters**

Ví dụ anh muốn khoảng cách giữa các từ trong một văn bản cách nhau 15 milimeters


{% highlight html linenos %}

p {word-spacing: .15mm;}

{% endhighlight %}

# **8. Đơn vị do pica**

1 pica sẽ bằng 12 points do đó 6 pica sẽ tương ứng là 1 inch. Ví dụ anh muốn kích thướt font chữ trong đoạn văn bản là 20 pica.

{% highlight html linenos %}

p {font-size: 20pc;}

{% endhighlight %}

# **9. Đơn vị do point**

Một point sẽ tương ứng với 1/72 inch. Ví dụ anh muốn font chữ có kích thướt 18pt 

{% highlight html linenos %}

body {font-size: 18pt;}

{% endhighlight %}

# **10. Đơn vị do pixel**

Ví dụ anh muốn khoảng cách của đoạn văn bản cách lề là 25 pixel.

{% highlight html linenos %}

      p {padding: 25px;}

{% endhighlight %}







