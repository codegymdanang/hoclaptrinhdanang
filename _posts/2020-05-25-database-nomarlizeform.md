---
layout: course-relationaldatabase
title:  Các bước chuẩn hoá dữ liệu
slug :  chuan-hoa-du-lieu
category: database
tags: [database]
summery: Các bước chuẩn hoá dữ liệu    
image: /images/blog/database.png
description : Chuẩn hoá dữ liệu là gì? Hiểu các quy luật 1NF, 2NF, 3NF, 4NF và BCNF. Hướng dẫn cách xây dựng một database chuẩn hoá dữ liệu, tìm hiểu các kỷ thuật chuẩn hoá database.
youtubeId: Thx8bBqIY28
---

# **Giới thiệu nội dung bài viết**

Chào các bạn, chắc các bạn gặp phải những khó khăn trong việc <b>tối ưu hoá dữ liệu trong database</b> ? Các bạn không biết mình nên
bắt đầu từ đâu khi xây dựng một <b>database</b> và làm thế nào để thiết kế một database tối ưu. Trong bài viết hôm nay anh sẽ trình bày
các kỷ thuật để có thể xây dựng được một database chuẩn.

<br>
# Tại sao phải cần chuẩn hoá dữ liệu
Để hiểu tại sao phải chuẩn hoá dữ liệu thì ta sẽ trả lời chuẩn hoá dữ liệu giúp được gì cho ta
1. Chuẩn hoá dữ liệu giúp ta giảm bớt sự dư thừa dữ liệu trong database, giúp chương trình chaỵ nhanh hơn , quản lý dể hơn
Anh lấy một ví dụ . Công ty Amazon nhờ team chúng ta xây dựng một ứng dụng kho hàng để quản lý sản phẩm . Nếu chúng ta
thiết kế không theo các bước chuẩn hoá chắc chắn 100% chúng ta sẽ tạo ra các tables và các column mà dữ liệu sẽ trùng lặp không cần thiết
Vậy các em hãy tưởng tượng 1 ngày ở Amazon cả hàng triệu sản phẩm được nhập kho thì lượng dữ liệu bị dư thừa là bao nhiêu .
Trong khi database có kích thước có giới hạn. Đồng thời khi ta truy vấn dữ liệu cũng sẽ làm cho câu query chậm đi. Tiếp đến khi mình bảo trì
sẽ gặp khó khăn vì không biết dữ liệu thừa đó xoá đi có ảnh hưởng chi đến các chức năng khác không ?

2. Giảm bớt ác lỗi xảy ra khi thực hiện các câu lệnh truy vấn xuống database như Insert , Update , Delete do dư
thừa dữ liệu gây ra.
<br>

<br>
# Vậy chuẩn hoá dữ liệu là gì ?
Là quá trình phân tích chia bảng thành những bảng nhỏ hơn dựa vào các quy luật chuẩn hoá.

<b>Có 4 dạnh  chuẩn hoá dữ liệu</b>  : 1NF , 2NF , 3 NF , 4NF , và dạng BCNF (Boyce Codd Normal Form) .

<br>
# Và bây giờ, hãy cùng xem code demo ở bên dưới để hiểu rõ hơn nhé .
{% include youtubePlayer.html id=page.youtubeId %}
