---
layout: course-relationaldatabase
title:  Sử dụng View
slug : database-view
category: database
tags: [database]
summery: View    
image: /images/blog/database.png
description : Trình bày view trong database là gì . Hướng dẫn cách sử dụng view trong database
youtubeId: mxYQUIMJ5Aw
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em, hôm nay chúng ta sẽ nói về chủ đề Stored Procedure trong database là gì nhé ?

# **1. Tạo View**

View là một dạng table giả hay table ảo không phải table thiệt. Mình thường tạo ra các table ảo để truy vấn dữ liệu cho nhanh.

Thông thường khi câu truy vấn lặp đi lặp lại nhiều lần ta thường tạo 1 View cho câu truy vấn đó.

- Cú pháp tạo VIEW

<br>
{% highlight sql linenos %}

CREATE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition; 

{% endhighlight %}

- Ví dụ ta tạo view sau

<br>
{% highlight sql linenos %}

CREATE VIEW [Brazil Customers] AS
SELECT CustomerName, ContactName
FROM Customers
WHERE Country = 'Brazil'; 

{% endhighlight %}

- Chúng ta thực thi câu lệnh để chạy VIEW

<br>
{% highlight sql linenos %}

SELECT * FROM [Brazil Customers]; 

{% endhighlight %}


- Ví dụ tạo view để xem sản phảm và giá trong bảng sản phẩm

<br>
{% highlight sql linenos %}

CREATE VIEW [Products Above Average Price] AS
SELECT ProductName, Price
FROM Products
WHERE Price > (SELECT AVG(Price) FROM Products); 

{% endhighlight %}


# **2. Update View**

- Cú pháp

<br>
{% highlight sql linenos %}

CREATE OR REPLACE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition; 
{% endhighlight %}

- Ví dụ

<br>
{% highlight sql linenos %}

CREATE OR REPLACE VIEW [Brazil Customers] AS
SELECT CustomerName, ContactName, City
FROM Customers
WHERE Country = 'Brazil';

{% endhighlight %}

# **3. Xoá View**

- Cú pháp

<br>
{% highlight sql linenos %}

DROP VIEW view_name; 

{% endhighlight %}

- Ví dụ

<br>
{% highlight sql linenos %}

DROP VIEW [Brazil Customers]; 

{% endhighlight %}


