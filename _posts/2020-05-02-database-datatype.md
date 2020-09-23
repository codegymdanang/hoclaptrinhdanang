---
layout: course-relationaldatabase
title:  Kiểu dữ liệu 
slug : database-datatype
category: database
tags: [database]
summery: Kiểu dữ liệu    
image: /images/blog/database.png
description : Trình bày kiểu dữ liệu của database. Hướng dẫn cách sử dụng kiểu dữ liệu trong database
youtubeId: tKLOuvrHCNw
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em, hôm nay chúng ta sẽ nói về chủ đề kiểu dữ liệu trong database là gì nhé ?

# **1. Kiểu dữ liệu**

Mỗi column(cột) trong database điều có kiểu dữ liệu để lưu trữ thông tin về đối tượng. Kiểu dữ liệu có thể lưu trong các cột có thể là kiểu số, chữ , tiền tệ hoặc ngày tháng v.v

Trong database có 3 kiểu dữ liệu chính là chuỗi, số và ngày tháng

# **2. Kiểu dữ liệu chuỗi**

{:class="table table-bordered"}
|  Kiểu dữ liệu  					|  Mô tả											    	|
|---								|---														|
|	Char(size)						| chứa từ 0 - 255 ký tự. mặc định là 1						|
|	Varchar(size)					| chứa từ 0 - 65535 ký tự									|
|	Binary(size)					| giống như char nhưng chứa giá trị là binary byte			|
|	VarBinary(size)					| giống như varchar nhưng chứa giá trị binary byte			|
|	TinyBlob						| chứa kiểu BLOB (cho những object lớn) max length là 255 bytes |
|	TinyText						| chứa giá trị chuỗi với max độ dài là 255 ký tự			|
|	Text(size)						| chứa giá trị chuỗi với max độ dài là 65.535 bytes			|
|	BLOB(size)						| chứa kiểu BLOBs có thể chứa đến 65.535 bytes dữ liệu		|
|	MediumText						| chứa kiểu string với giá trị max là 16,777,215 ký tự		|
|	MediumBlob						| chứa kiểu BLOB có thể chứa đến 16,777,215 bytes 			|
|	LongText						| chứa kiểu string chứa đến 4,294,967,295 ký tự				|
|	LongBlob						| chứa đến 4,294,967,295 bytes dữ liệu						|

# **3. Kiểu dữ liệu số**

{:class="table table-bordered"}
|  Kiểu dữ liệu  					|  Mô tả											    	|
|---								|---														|
|	BIT								| chứa số từ 1 đến 64. giá trị mặc định là 1				|
|	TINYINT(size)					| chứa từ 0 đến 255											|
|	BOOL							| 0 là sai và 1 là đúng										|
|	BOOLEAN							| giống như BOOL 											|
|	SMALLINT(size)					| chứa từ 0 đến 65535										|
|	MEDIUMINT(size)					| chứa từ 0 đến 16777215									|
|	INT(size)						| chứa từ 0 đến 4294967295									|
|	INTEGER(size)					| giống như INT 											|
|	BIGINT(size)					| chứa từ 0 đến 18446744073709551615						|
|	FLOAT(p)						| chứa kiểu dạng tiền tệ như $2.1. p là tổng con số sau dấu . |
|	DOUBLE(p)						| nếu p là từ 0 -> 24 là kiểu float còn từ 25->53 là DOUBLE | 

# **4. Kiểu dữ liệu ngày**

{:class="table table-bordered"}
|  Kiểu dữ liệu  					|  Mô tả											    	|
|---								|---														|
|	DATE							| Kiểu ngày với đinh danh là YYYY-MM-DD						|
|	DATETIME						| Kiểu ngày và giờ với định dạng Format: YYYY-MM-DD hh:mm:ss|
|	TIMESTAMP 						| Kiểu định dạng YYYY-MM-DD hh:mm:ss cho giờ hiện tại của hệ thống |
|	TIME 							| Định dạng  hh:mm:ss										|
|	YEAR							| Đinh đạng 4 chữ số từ năm 1901 to 2155






