---
layout: course-relationaldatabase
title:  Các hàm tổng hợp SQL 
slug : database-sql-aggreate
category: database
tags: [database]
summery: Hàm tổng hợp    
image: /images/blog/database.png
description : Trình bày các hàm tổng hợp trong database. Hướng dẫn cách sử dụng các hàm tổng hợp trong database
youtubeId: tKLOuvrHCNw
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em, hôm nay chúng ta sẽ nói về các hàm tổng hợp trong database là gì nhé ?

- Ví dụ ta có table sau đây

{:class="table table-bordered"}
|  CustomerName                     |  ContactName      |   Address                     |   City        |   PostalCode  |   Country     |
|---                                |---                |---                            |---            |---            |---            |
|Alfreds Futterkiste                |Maria Anders       |Obere Str. 57                  |   Berlin      |   12209       |   Germany     |       
|Ana Trujillo Emparedados y helados |Ana Trujillo       |Avda. de la Constitución 2222  |   México D.F. |   05021       |   Mexico      |
|Antonio Moreno Taquería            |Antonio Moreno     |Mataderos 2312                 |   México D.F. |   05023       |   Mexico      |
|Around the Horn                    |Thomas Hardy       |120 Hanover Sq.                |   London      |   WA1 1DP     |   UK          |
|Berglunds snabbköp                 |Christina Berglund |Berguvsvägen 8                 |   Luleå       |   S-958 22    |   Sweden      |


# **1. SQL Limit**

Chúng ta sử dụng Limit để chỉ rõ số dòng sẽ được trả về.

- Cú pháp

<br>
{% highlight sql linenos %}

SELECT column_name(s)
FROM table_name
WHERE condition
LIMIT number;

{% endhighlight %}

- Ví dụ chúng ta chỉ lấy 3 dòng

<br>
{% highlight sql linenos %}

SELECT * FROM Customers
LIMIT 3; 

{% endhighlight %}

- Chúng ta có thể sử dụng %. Ví dụ mình muốn lấy 50% số dòng

<br>
{% highlight sql linenos %}

SELECT TOP 50 PERCENT * FROM Customers;

{% endhighlight %}

- Chúng ta có thể kết hợp mệnh đề where vào trong câu truy vấn

<br>
{% highlight sql linenos %}

SELECT * FROM Customers
WHERE Country='Germany'
LIMIT 3; 

{% endhighlight %}

# **2. SQL Min và Max**

- Cú pháp
<br>
{% highlight sql linenos %}

SELECT MIN(column_name)
FROM table_name
WHERE condition;

{% endhighlight %}

<br>
{% highlight sql linenos %}

SELECT MAX(column_name)
FROM table_name
WHERE condition;

{% endhighlight %}

- Ví dụ lấy ra những kết quả có giá thấp nhất

<br>
{% highlight sql linenos %}

SELECT MIN(Price) AS SmallestPrice
FROM Products;

{% endhighlight %}

- Ví dụ lấy ra những kết quả có giá cao nhất
<br>
{% highlight sql linenos %}

SELECT MAX(Price) AS LargestPrice
FROM Products; 

{% endhighlight %}

# **3. SQL Count AVG SUM**

Chúng ta sử dụng Count để đếm số lượng kết quả trả về

- Cú pháp

<br>
{% highlight sql linenos %}

SELECT COUNT(column_name)
FROM table_name
WHERE condition; 

{% endhighlight %}

- Ví dụ đến số lượng sản phẩm có là bao nhiêu

<br>
{% highlight sql linenos %}

SELECT COUNT(ProductID)
FROM Products;

{% endhighlight %}

Chúng ta sử dụng AVG để lấy giá trị trung bình

- Cú pháp

<br>
{% highlight sql linenos %}

SELECT AVG(column_name)
FROM table_name
WHERE condition; 
{% endhighlight %}

- Ví dụ lấy giá trung bình của tổng sản phẩm

<br>
{% highlight sql linenos %}
SELECT AVG(Price)
FROM Products;
{% endhighlight %}

Chúng ta sử dụng Sum để tính tổng

- Cú pháp

<br>
{% highlight sql linenos %}

SELECT SUM(column_name)
FROM table_name
WHERE condition; 

{% endhighlight %}

- Ví dụ tính tổng số đơn hàng

<br>
{% highlight sql linenos %}

SELECT SUM(Quantity)
FROM OrderDetails; 

{% endhighlight %}










