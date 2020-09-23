---
layout: course-relationaldatabase
title:  Ràng buộc dữ liệu
slug : database-constraints
category: database
tags: [database]
summery: Ràng buộc dữ liệu    
image: /images/blog/database.png
description : Trình bày ràng buộc dữ liệu trong database. Hướng dẫn cách sử dụng ràng buộc dữ liệu  trong database
youtubeId: tKLOuvrHCNw
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em, hôm nay chúng ta sẽ nói về chủ đề ràng buộc dữ liệu trong database là gì nhé ?

# **1. Ràng buộc dữ liệu**

Chúng ta sử dụng ràng buộc dữ liệu khi tạo ra bảng hoặc chỉnh sửa bảng. Anh lấy ví dụ khi mình có trường dữ liệu là số điện thoại và mình muốn trường đó không được phép rỗng thì mình sẽ sử dụng từ khoá constraint để bắt buộc người dùng phải nhận vào

- Cú pháp

<br>
{% highlight sql linenos %}

CREATE TABLE table_name (
    column1 datatype constraint,
    column2 datatype constraint,
    column3 datatype constraint,
    ....
);

{% endhighlight %}


# **2. Constraint NOT NULL**

- Ví dụ sau ta ràng buộc trường ID là không được NULL

<br>
{% highlight sql linenos %}

CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255) NOT NULL,
    Age int
);
{% endhighlight %}

- Ví dụ cho Alter table

<br>
{% highlight sql linenos %}

ALTER TABLE Persons

MODIFY Age int NOT NULL; 

{% endhighlight %}

# **3. Constraint Unique**

Khi mình muốn dữ liệu của trường đó là duy nhất không bị trùng.

<br>
{% highlight sql linenos %}

CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    CONSTRAINT UC_Person UNIQUE (ID,LastName)
); 

{% endhighlight %}

# **4. Constraint Khoá chính**

Ta sử dụng từ khoá PRIMARY KEY để ràng buộc trường ID là khoá chính. Dữ liệu là duy nhất và không được trùng lặp. Trong table luôn luôn phải có 1 khoá chính.

<br>
{% highlight sql linenos %}

CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    PRIMARY KEY (ID)
); 

{% endhighlight %}

# **5. Constraint Khoá phụ**

Ta sử dụng từ khoá FOREIGN KEY để khai báo khoá phụ và dùng để tham chiếu tới một bảng khác

<br>
{% highlight sql linenos %}

CREATE TABLE Orders (
    OrderID int NOT NULL,
    OrderNumber int NOT NULL,
    PersonID int,
    PRIMARY KEY (OrderID),
    FOREIGN KEY (PersonID) REFERENCES Persons(PersonID)
); 
{% endhighlight %}

# **6. Constraint Check**

Anh lấy ví dụ mình muốn kiểm tra trường Age phải lớn hơn 18 mới cho phép được nhập vào table. Nếu nhỏ hơn 18 thì không được. Chúng ta dùng từ khoá Check để làm việc này.

<br>
{% highlight sql linenos %}

CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    CHECK (Age>=18)
);

{% endhighlight %}

# **7. Constraint Default**

Khi ta muốn tạo một giá trị mặc định cho một trường. Ví dụ anh muốn đặt giá trị mặc định cho trường City là Sandnes nếu người dùng không nhập giá trị vào thì sẽ lấy giá trị Sandnes.

<br>
{% highlight sql linenos %}

CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    City varchar(255) DEFAULT 'Sandnes'
); 

{% endhighlight %}

# **8. Constraint Index**

Sử dụng Index để đánh các chỉ mục của table. Index giống như trang mục lục của một cuốn sách. Dựa vào Index thì dể tìm kiếm thông tin hơn. Hãy tưởng tượng cuốn sách có 1000 trang. Nhờ vào index thì chúng ta có thể dể dàng tìm kiếm tới phần cần tìm trong cuốn sách.

- Cú pháp

<br>
{% highlight sql linenos %}

CREATE UNIQUE INDEX index_name
ON table_name (column1, column2, ...); 

{% endhighlight %}

- Ví dụ

{% highlight sql linenos %}

CREATE INDEX idx_lastname
ON Persons (LastName); 

{% endhighlight %}

- Xoá Index

{% highlight sql linenos %}

ALTER TABLE table_name
DROP INDEX index_name; 

{% endhighlight %}

# **9. Constraint Auto Increment**

Chúng ta sử dụng từ khoá Auto Increment để tăng tự động giá trị cho một trường trong bảng. Trường này thường là khoá chính. Tăng tự động có nghĩa là lúc đầu giá trị nó là 1. Khi ta thêm một dòng mới thì tự động trường đó tằng giá trị lên 2. Ta hoàn toàn có thể chỉnh sửa bước nhảy đơn vị tăng tự động.

{% highlight sql linenos %}

CREATE TABLE Persons (
    Personid int NOT NULL AUTO_INCREMENT,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    PRIMARY KEY (Personid)
); 

{% endhighlight %}



















































