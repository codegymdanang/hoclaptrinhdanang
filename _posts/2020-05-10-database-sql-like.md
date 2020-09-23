---
layout: course-relationaldatabase
title:  SQL Like 
slug : database-sql-aggreate
category: database
tags: [database]
summery: Toán tử Like    
image: /images/blog/database.png
description : Trình bày các sql like trong database. Hướng dẫn cách sử dụng  sql like trong database
youtubeId: tKLOuvrHCNw
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em, hôm nay chúng ta sẽ nói về sql like trong database là gì nhé ?

# **1. Toán tử Like**

Toán tử Like hay được sử dụng chung với các mệnh để where để tìm các dữ liệu dự trên một điều kiện được định dạng trước.

- Cú pháp 
<br>
{% highlight sql linenos %}

SELECT column1, column2, ...
FROM table_name
WHERE columnN LIKE pattern;

{% endhighlight %}

Ví dụ toán tử like sử dụng % và _

- % có nghĩa là 0 hoặc nhiều ký tự
- _ chỉ là 1 ký tự


{:class="table table-bordered"}
|  Toán tử  						|  Mô tả										|
|---								|---											|
|	WHERE CustomerName LIKE 'a%'	| tìm các giá trị bắt đầu bằng chữ a theo sau là chữ gì cũng được	|
|	WHERE CustomerName LIKE '%a'	| chữ cuối phải là chữ a trước đó chữ gì cũng được |
|	WHERE CustomerName LIKE '%or%'	| bắt buột chữ ở giữa là chữ or trước đó hoặc sau đó chữ gì cũng được |
|	WHERE CustomerName LIKE '_r%'	| chữ r bắt buộc phải nằm ở vị trí thứ 2							|
|	WHERE CustomerName LIKE 'a_%'	| chữ đầu tiền là chữ a và tối thiểu 2 ký tự |
|	WHERE CustomerName LIKE 'a__%'	| chữ đầu tiền là chữ a và tối thiểu 3 ký tự |
|	WHERE ContactName LIKE 'a%o'	| bắt đầu là chử a và kết thúc là chữ o |


- Ví dụ tìm tất cả tên khách hàng bắt đầu là chữ a

<br>
{% highlight sql linenos %}

SELECT * FROM Customers
WHERE CustomerName LIKE 'a%'; 

{% endhighlight %}

- Ví dụ tìm tất cả khách hàng kết thúc là chữ a

<br>
{% highlight sql linenos %}

SELECT * FROM Customers
WHERE CustomerName LIKE '%a'; 

{% endhighlight %}

# **2. Toán tử IN**

Chúng ta sử dụng toán tử IN để kiểm tra nhiều giá trị trong mệnh đề WHERE

- Cú pháp
<br>
{% highlight sql linenos %}

SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1, value2, ...); 

{% endhighlight %}

- Ví dụ tìm tất cả khách hàng có Country là Germany hoặc France hoặc UK

<br>
{% highlight sql linenos %}

SELECT * FROM Customers
WHERE Country IN ('Germany', 'France', 'UK');

{% endhighlight %}

# **3. Toán tử BETWEEN**

Chúng ta sử dụng toán tử Between để kiểm tra điều kiện trong 1 range (khoảng).

- Cú pháp

<br>
{% highlight sql linenos %}

SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value1 AND value2; 

{% endhighlight %}

- Ví dụ tìm các sản phẩm có giá từ 10 tới 20 đồng

<br>
{% highlight sql linenos %}

SELECT * FROM Products
WHERE Price BETWEEN 10 AND 20;

{% endhighlight %}

- Ngoài ra chúng ta có thể sử dụng NOT Between. Ví dụ lấy tất cả sản phẩm có giá không nằm trong 10 và 20 đồng.

<br>
{% highlight sql linenos %}

SELECT * FROM Products
WHERE Price NOT BETWEEN 10 AND 20;

{% endhighlight %}

# **4. Định danh**

Chúng ta muốn tạo một cái tên cho table hoặc column của chúng ta thông qua từ khoá AS

- Cú pháp

<br>
{% highlight sql linenos %}

SELECT column_name AS alias_name
FROM table_name;

{% endhighlight %}

- Ví dụ ta muốn đặt tên cho cột CustomerID là ID và CustomerName là Customer trong kết quả trả về

<br>
{% highlight sql linenos %}

SELECT CustomerID AS ID, CustomerName AS Customer
FROM Customers; 
{% endhighlight %}




