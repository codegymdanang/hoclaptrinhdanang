---
layout: course-spring-web
title: Session và Cookie
slug : spring-session-cookie 
category: laptrinhspring
tags: [spring-web]
summery: Session và Cookie
image: /images/blog/spring.png
featureImage: /images/post/javacore/feature_sessioncookie.png
description : Sử dụng Session và Cookie trong lập trình Spring. Hướng dẫn cách Session và Cookie trong lập trình các dự án về Spring.
youtubeId: ym4-rU9R6fM
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**
Chào bạn, chắc khá nhiều bạn đang học lập trình không phân biệt được sự khác nhau giữa session và cookie . Khi nào thì dùng chúng
Hôm nay anh sẽ trình bày nguyên lý và sự khác nhau của <b>session</b> và <b>cookie</b> cũng như khi nào mình sẽ sử dụng nó.

<br>
# **1. Session là gì**

Một <b>session</b> hay còn gọi là một phiên làm việc. Nó  là cách giao tiếp giữa client (trình duyệt web) với server.
Một session bắt đầu khi client gửi request đến sever, nó tồn tại xuyên suốt từ trang này đến trang khác trong ứng dụng và chỉ kết thúc khi hết thời gian timeout hoặc khi bạn đóng ứng dụng tắt trình duyệt .
Giá trị của session sẽ được lưu trong một tệp tin trên máy chủ. Chúng chỉ nên lưu trữ những thông tin tạm thời trong session
Với mỗi session sẽ được cấp phát một định danh duy nhất SessionID. Khi kết thúc một phiên làm việc và bắt đầu một phiên mới,mình sẽ nhận được một session ID khác

Sau khi server tạo các giá trị session, server sẽ tạo ra một tệp tin <b>cookie</b> lưu trên trình duyệt của người dùng ứng với session đó. Như vậy chỉ cần so sánh tệp tin cookie bên phía client được gửi lên sever và tệp session được lưu trên server
để xem làm trình duyệt đó là mới hay cũ.

<br>
# **2. Cookie là gì**

<b>Cookie</b> cũng được dùng để lưu những thông tin tạm thời. Tệp tin cookie sẽ được truyền từ server tới browser và được lưu trữ trên máy tính của bạn khi bạn truy cập vào ứng dụng. Như vậy dù có tắt browser cũng không mất đi các giá trị vì chúng ta đã lưu nó trên máy tính của mình.


<br>
# **3. So sánh session và cookie**

{:class="table table-bordered"}
 |  	 Cookie                                             |   Session	                                        |
 |---	                                                    |---	     	                                    |
 |   Cookie được lưu trữ trên trình duyệt của người dùng.   |   Session không được lưu trữ trên trình duyệt.    |                                            
 |  Dữ liệu cookie được lưu trữ ở phía client.| Dữ liệu session được lưu trữ ở phía server. |
 |  Dữ liệu cookie dễ dàng sửa đổi hoặc đánh cắp khi chúng được lưu trữ ở phía client      |   Dữ liệu session không dễ dàng sửa đổi vì chúng được lưu trữ ở phía máy chủ.|
 |  Dữ liệu cookie có sẵn trong trình duyệt đến khi expired.   | Sau khi đóng trình duyệt sẽ hết phiên làm việc (session)   |



<br>
# **4. Session và Cookie được dùng ở đâu**

Chúng ta thường<b>sử dụng Session và Cookie để lưu tạm các giá trị</b> tại một thời điểm nào đó trong một khoản thời gian ngắn và nhất định. Thông thường trong các ứng dụng mình có thể lưu  dữ liệu ở database (nếu dữ liệu muốn lưu từ 1 năm trở lên), ngoài database chúng ta có thể lưu trữ trong file hoặc lưu trữ tạm trên RAM. 

Những chức năng lưu giá trị tạm thời tại một thời điểm ngắn thì mình có thể dùng session và cookie để làm việc này. Anh ví dụ như chức năng giỏ hàng trong các ứng dụng mua hàng. Ví dụ như ứng dụng mua hàng lazada , mình có thể chọn sản phẩm mình cần mua sau đó thêm nó vào giỏ hàng, sau đó mình tiếp tục mua các sản phẩm khác. Khi thanh toán giỏ hàng thì mình sẽ duyệt qua một mảng danh sách các sản phẩm mà mình đã lưu trước đó. Như vậy mình sẽ dùng session để lưu trữ danh sách các sản phẩm. Nhờ có session mà mình có thể lưu tạm thời dữ liệu và thao tác với nó. Vì các dữ liệu lưu trong session chỉ tồn tại trong 1 phiên giao dịch (khi tắt browser thì sẽ mất hết giá trị lưu trong session) nên mình thường sử dụng chung session với cookie để lưu trữ dữ liệu lâu hơn. Các em tưởng tượng nếu mình dùng session ở trên để lưu giỏ hàng thì khi người dùng tắt máy các sản phẩm trong giỏ hàng sẽ bị mất. Muốn giữ lại các sản phẩm mà người dùng đã chọn cho dù họ tắt trình duyệt hoặt tắt máy. Hôm sau họ vào thì họ vẫn thấy được các sản phẩm trong giỏi hàng thì mình sẽ kết hợp với cookie để lưu giá trị . Vì cookie sẽ lưu trên máy người dùng nên nó sẽ không mất đi, nó mất đi khi thời gian sống hết hạn(cái này do lập trình viên cấu hình). Chính vì vậy mà các em thấy các trang web mua bán sản phẩm họ thường kết hợp cả hai để tăng doanh thu. Vì hôm nay mình chọn sản phẩm ở giỏ hàng mà mình chưa mua thì ngày mai khi mình vào lại thì trang web sẽ nhắc nhở mình có các sản phẩm cần thanh toán.

Như các em thấy các ứng dụng ngày nay khi muốn vào ứng dụng thì nó bắt mình đăng nhập tên và mật khẩu , sau đó có thêm cái checkbox (nhớ đăng nhập). Nếu mình chọn cái checkbox đó thì lần sau mình không cần phải đăng nhập tên và mật khẩu nữa. Vì lúc này mình đã dùng cookie để lưu lại lần đăng nhập đầu tiên của người dùng. Cookie này sẽ hết hạn (ví dụ cookie sống trong vòng 30 ngày) thì lúc đó người dùng sẽ phải đăng nhập lại. Anh lấy ví dụ như ứng dụng facebook mình chỉ đăng nhập lần đầu tiên thôi lần sau mình vào thẳng luôn trang chủ của facebook mà không cần phải điền lại tên và mật khẩu.



<br>
# **5. Và bây giờ, hãy cùng xem code demo ở bên dưới để hiểu rõ hơn nhé**

{:refdef: style="text-align: center;"}
{% include youtubePlayer.html id=page.youtubeId %}
{: refdef}
