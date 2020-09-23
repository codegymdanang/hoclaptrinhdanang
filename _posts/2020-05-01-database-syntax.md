---
layout: course-relationaldatabase
title:  Cú pháp
slug : database-syntax
category: database
tags: [database]
summery: Cú pháp    
image: /images/blog/database.png
description : Trình bày cú pháp của database. Hướng dẫn cách sử dụng cú pháp trong database
youtubeId: tKLOuvrHCNw
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em, hôm nay chúng ta sẽ nói về chủ đề Cú pháp trong database là gì nhé ?

# **1. Database Table**

Database (Cơ sở dữ liệu) thường chứa 1 hoặc nhiều table. Mỗi table được định nghĩa bởi một cái tên (Ví dụ Customer hoặc Order). Table chứa nhiều dòng, mỗi dòng trong table là chứ dữ liệu.

Trong bài tutorial sau đây mình sẽ thực hành và làm ví dụ về 1 table có tên là Customers. Với nội dung như sau

{:class="table table-bordered"}
|  CustomerName  					|  ContactName	    |   Address	  					| 	City		|	PostalCode	|	Country		|
|---	            				|---	            |---	     					|---			|---			|---			|
|Alfreds Futterkiste				|Maria Anders		|Obere Str. 57					|	Berlin		|	12209		|	Germany		|		
|Ana Trujillo Emparedados y helados	|Ana Trujillo		|Avda. de la Constitución 2222	|	México D.F.	|	05021		|	Mexico		|
|Antonio Moreno Taquería			|Antonio Moreno		|Mataderos 2312					|	México D.F.	|	05023		|	Mexico		|
|Around the Horn					|Thomas Hardy		|120 Hanover Sq.				|	London		|	WA1 1DP		|	UK			|
|Berglunds snabbköp					|Christina Berglund	|Berguvsvägen 8					|	Luleå		|	S-958 22	|	Sweden		|

Table (bảng) Customer chứa 5 records (5 dòng). Mỗi dòng là thông tin của 1 khách hàng. Chúng ta có 7 columns (cột). Mỗi cột là một thuộc tính của khách hàng.

# **2. SQL Statement**

Hầu hết các hành động ta thực hiện trên database (cơ sở dữ liệu) thông qua các câu lệnh SQL.

Ví dụ đây là câu lệnh hiển thị danh sách khách hàng có trong bảng Customer.


<br>
{% highlight sql linenos %}

SELECT * FROM Customers;

{% endhighlight %}

Mysql không phân biệt chữ hoa chữ thường chúng ta viết select thì cũng giống như SELECT. Sau mỗi câu lệnh SQL thì ta sử dụng dấu ; để kết thúc câu lệnh.

Câu lệnh SQL được chia ra thành 3 loại DDL , DML và DCL 

- Data Definition Language (DDL) : Các câu lệnh định nghĩa cấu trúc để lưu trữ dữ liệu.

+ CREATE to create a new table or database.
+ ALTER for alteration.
+ Truncate to delete data from the table.
+ DROP to drop a table.
+ RENAME to rename a table. 

- Data Manipulation Language (DML): dùng để truy vấn, cập nhật và thêm dữ liệu trong table
+ INSERT to insert a new row.
+ UPDATE to update an existing row.
+ DELETE to delete a row.
+ MERGE for merging two rows or two tables.

- Data Control Language (DCL): Các câu lệnh dùng để quản lý permission trong cơ sở dử liệu

+ COMMIT to permanently save.
+ ROLLBACK to undo the change.
+ SAVEPOINT to save temporarily.





