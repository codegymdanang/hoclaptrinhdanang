---
layout: course-relationaldatabase
title:  Các câu lệnh cấu trúc DLL
slug : database-dll
category: database
tags: [database]
summery: Câu lệnh DLL    
image: /images/blog/database.png
description : Trình bày các câu lệnh dll của database. Hướng dẫn cách sử dụng các câu lệnh dll trong database
youtubeId: tKLOuvrHCNw
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em, hôm nay chúng ta sẽ nói về chủ đề các câu lệnh dll trong database là gì nhé ?

# **1. Các câu lệnh DLL**

Data Definition Language (DDL) : Các câu lệnh định nghĩa cấu trúc để lưu trữ dữ liệu. Chúng ta sử dụng các câu lệnh này dùng cho việc thao tác trên database(cơ sở dữ liệu), table(bảng), các trường (cols)

# **2. Tạo Database**

Chúng ta dùng từ khoá CREATE DATABASE để tạo cơ sở dữ liệu. 

- Cú pháp

<br>
{% highlight sql linenos %}

CREATE DATABASE databasename; 

{% endhighlight %}

- Ví dụ tạo database tên testDB

<br>
{% highlight sql linenos %}

CREATE DATABASE testDB;

{% endhighlight %}

# **3. Xoá Database**

Chúng ta sử dụng từ khoá DROP DATABASE để xoá cơ sở dữ liệu

- Cú pháp

<br>
{% highlight sql linenos %}

DROP DATABASE databasename; 

{% endhighlight %}

- Ví dụ xoá database tên testDB

<br>
{% highlight sql linenos %}

DROP DATABASE testDB;

{% endhighlight %}

# **4. Tạo Bảng**

Chúng ta sử dụng từ khoá CREATE TABLE  để tạo bảng trong cơ sở dữ liệu

- Cú pháp

<br>
{% highlight sql linenos %}

CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
)

{% endhighlight %}

- Ví dụ 

<br>
{% highlight sql linenos %}

CREATE TABLE Persons (
    PersonID int,
    LastName varchar(255),
    FirstName varchar(255),
    Address varchar(255),
    City varchar(255)
);
{% endhighlight %}

# **5. Xoá Bảng**

Chúng ta sử dụng từ khoá DROP TABLE  để xoá bảng trong cơ sở dữ liệu

- Cú pháp

<br>
{% highlight sql linenos %}

DROP TABLE table_name; 

{% endhighlight %}

- Ví dụ 

<br>
{% highlight sql linenos %}

DROP TABLE Shippers;

{% endhighlight %}

# **5. Xoá hết dữ liệu trong Bảng**

Chúng ta sử dụng từ khoá TRUNCATE TABLE  để xoá hết các dữ liệu trong bảng. Khác với Drop table ở chỗ là TRUNCATE chỉ xoá dữ liệu còn cấu trúc bảng vẫn giữ nguyên, còn Drop thì nó xoá hết tất cả mọi thứ về cấu trúc bảng và dữ liệu.

- Cú pháp

<br>
{% highlight sql linenos %}

TRUNCATE TABLE table_name; 

{% endhighlight %}

- Ví dụ 

<br>
{% highlight sql linenos %}

TRUNCATE TABLE Shippers;

{% endhighlight %}

# **6. Chỉnh sử lại Bảng**

Chúng ta sử dụng ALTER TABLE để chỉnh sửa, xoá , thêm lại các col trong table đã có sẳn.

- Cú pháp sau đây thêm 1 column vào bảng có sẳn

<br>
{% highlight sql linenos %}

ALTER TABLE table_name
ADD column_name datatype;

{% endhighlight %}

- Ví dụ 

<br>
{% highlight sql linenos %}

ALTER TABLE Customers
ADD Email varchar(255);
{% endhighlight %}

- Cú pháp sau đây xoá 1 column vào bảng có sẳn

<br>
{% highlight sql linenos %}

ALTER TABLE table_name
DROP COLUMN column_name; 

{% endhighlight %}

- Ví dụ 

<br>
{% highlight sql linenos %}

ALTER TABLE Customers
DROP COLUMN Email;

{% endhighlight %}

- Cú pháp sau đây thay đổi kiểu dữ liệu 1 column vào bảng có sẳn

<br>
{% highlight sql linenos %}

ALTER TABLE table_name
MODIFY COLUMN column_name datatype; 

{% endhighlight %}

- Ví dụ 

<br>
{% highlight sql linenos %}

ALTER TABLE Customers
MODIFY COLUMN Email varchar(255); 

{% endhighlight %}





