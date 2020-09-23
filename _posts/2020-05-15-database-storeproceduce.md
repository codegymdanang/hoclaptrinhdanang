---
layout: course-relationaldatabase
title:  Sử dụng Stored Procedure
slug : stored-procedure
category: database
tags: [database]
summery: Stored Procedure    
image: /images/blog/database.png
description : Trình bày Stored Procedure trong database là gì . Hướng dẫn cách sử dụng Stored Procedure trong database
youtubeId: mxYQUIMJ5Aw
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em, hôm nay chúng ta sẽ nói về chủ đề Stored Procedure trong database là gì nhé ?

# **1. Stored Procedure**

Cũng giống như lập trình vậy, chúng ta có thể tạo các phương thức các hàm trong SQL khai báo tên hàm các đối số. Sau đó chúng ta có thể gọi hàm và nhận lấy giá trị

- Cú pháp tạo stored procedure

<br>
{% highlight sql linenos %}

CREATE PROCEDURE procedure_name
AS
sql_statement
GO;

{% endhighlight %}

- Chạy hay thực thi 1 stored procedure

<br>
{% highlight sql linenos %}

EXEC procedure_name; 

{% endhighlight %}

- Ví dụ ta có bảng dữ liệu sau

{:class="table table-bordered"}
|  CustomerName  					|  ContactName	    |   Address	  					| 	City		|	PostalCode	|	Country		|
|---	            				|---	            |---	     					|---			|---			|---			|
|Alfreds Futterkiste				|Maria Anders		|Obere Str. 57					|	Berlin		|	12209		|	Germany		|		
|Ana Trujillo Emparedados y helados	|Ana Trujillo		|Avda. de la Constitución 2222	|	México D.F.	|	05021		|	Mexico		|
|Antonio Moreno Taquería			|Antonio Moreno		|Mataderos 2312					|	México D.F.	|	05023		|	Mexico		|
|Around the Horn					|Thomas Hardy		|120 Hanover Sq.				|	London		|	WA1 1DP		|	UK			|
|Berglunds snabbköp					|Christina Berglund	|Berguvsvägen 8					|	Luleå		|	S-958 22	|	Sweden		|


- Chúng ta tạo 1 stored procedure có tên là SelectAllCustomers

<br>
{% highlight sql linenos %}

CREATE PROCEDURE SelectAllCustomers
AS
SELECT * FROM Customers
GO;
{% endhighlight %}

- Chúng ta thực thi

<br>
{% highlight sql linenos %}

EXEC SelectAllCustomers;
{% endhighlight %}

# **2. Stored Procedure với tham số**

Giống như phương thức (hàm) trong lập trình, thì phướng thức có tham số thì stored procedure cũng có tham số

- Ví dụ tạo một stored procedure có tham số city 

<br>
{% highlight sql linenos %}

CREATE PROCEDURE SelectAllCustomers @City nvarchar(30)
AS
SELECT * FROM Customers WHERE City = @City
GO;
{% endhighlight %}

- Chúng ta thực thi stored procedure và truyền tham số city là London vào


<br>
{% highlight sql linenos %}

EXEC SelectAllCustomers @City = 'London'; 

{% endhighlight %}

# **3. Stored Procedure với nhiều tham số**

<br>
{% highlight sql linenos %}
CREATE PROCEDURE SelectAllCustomers @City nvarchar(30), @PostalCode nvarchar(10)
AS
SELECT * FROM Customers WHERE City = @City AND PostalCode = @PostalCode
GO;
{% endhighlight %}

<br>
{% highlight sql linenos %}
EXEC SelectAllCustomers @City = 'London', @PostalCode = 'WA1 1DP'; 
{% endhighlight %}





