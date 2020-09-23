---
layout: course-java
title: Toán tử
slug : toan-tu
category: laptrinhjava
tags: [java core]
summery: Toán tử  
image: /images/blog/java.png

description : Hiểu về Toán tử là gì trong lập trình hướng đối tượng trong lập trình? Giải thích các khái niệm về Toán tửliệu trong lập trình hướng đối tượng. Lợi ích của việc sử dụng Toán tử liệu trong lập trình hướng đối tượng trong lập trình.
youtubeId: fR05ShUphxA
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em. Hôm nay chủ đề của chúng ta sẽ về Toán tử trong lập trình java.

<br>
# **Toán tử là gì**

Chúng ta sử dụng toán tử để thực hiện các phép tính toán học trên giá trị và biến.

# **1.  Toán tử số số học**

{:class="table table-bordered"}
|  Toán tử		  	 		|  Ví dụ		            		|   kết quả			|
|---	                 	|---	                        	|---	     	    |
| +			         		|	x = 5 + 5						| 	x = 10			|
| -							|	x = 10 - 3						|	x = 7			|
| *							|	x -= 3 * 3						|	x = 6			|
| /							|	x = 3/1							|	x = 3			|
| % 						|	x = 10%5						|	x = 2			|
| ++ 						|	++x								|	x tăng thêm 1 giá trị			|
| -- 						|	--x								|	x giảm đi 1 giá trị		|

# **2.  Toán tử số gán**

{:class="table table-bordered"}
|  Toán tử		  	 		|  Ví dụ		            		|   kết quả			|
|---	                 	|---	                        	|---	     	    |
| =			         		|	x = 5							| 	x = 5			|
| +=						|	x += 3							|	x = x + 3		|
| -=						|	x -= 3							|	x = x - 3		|
| *=						|	x *= 3							|	x = x * 3		|
| /= 						|	x /= 3							|	x = x / 3		|
| %= 						|	x %= 3							|	x = x % 3		|
| &=						|	x &= 3							|	x = x & 3		|
| \|= 						|	x |= 3							|	x = x | 3		|
| ^=		\				|	x ^= 3							|	x = x ^ 3		|
| >>=						|	x >>= 3							|	x = x >> 3		|
| <<=						|	x <<= 3							|	x = x << 3		|


# **3.  Toán tử  so sánh**

{:class="table table-bordered"}
|  Toán tử		  	 		|  Ví dụ		            		|   Mô tả					|
|---	                 	|---	                        	|---	     	    		|
| ==			         	|	x == y							| 	so sánh bằng			|
| !=						|	x! = y							|	so sánh không bằng		|
| >							|	x > y 							|	so sánh lớn hơn			|
| <							|	x < y 							|	so sánh nhỏ hơn			|
| >= 						|	x >= y 							|	so sánh lớn hơn hoặc bằng			|
| <= 						|	x <= y							|	so sánh nhỏ hơn hoặc bằng			|

# **4.  Toán tử logic**

{:class="table table-bordered"}
|  Toán tử		  	 		|  Ví dụ		            		|   Mô tả											|
|---	                 	|---	                        	|---	     	    								|
| &&			         	|	x < 5 &&  x < 10				| 	trả về true nếu cả 2 mệnh đề cùng đúng 			|
| \|\|						|	x < 5 || x < 4					|	trả về truế nếu 1 trong 2 mệnh đề là đúng		|
| !							|	!(x < 5 && x < 10) 				|	phủ định lại giá trị trong  kết quả 			|

# **6.  Toán tử Bit**

{:class="table table-bordered"}
|  Toán tử		  	 		|  Ví dụ		   |   Mô tả			|		Kết quả		|	Giá trị			|	
|---	                 	|---	           |---	     			|---				|---				|
| &			         		|	5 & 1		   | 0101 & 0001		|		0001		|		 1			|
| \|							|	5 | 1		   | 0101 | 0001		|		0101		|		 5			|
| ~							|	~ 5			   |~0101				|		1010		|		10			|
| ^							|	5 ^ 1		   |0101 ^ 0001			|		0100		|		4			|
| <<						|	9 << 1		   | 1001 << 1			|		0010		|		2			|
| >>						|	9 >> 1		   | 1001 >> 1			|		1100		|		12			|
| >>>						|	9 >>> 1		   | 1001 >>> 1			|		0100		|		4			|















