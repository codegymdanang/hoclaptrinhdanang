---
layout: course-spring-web
title: Phân biệt Request Param và PathVariable
slug : request-param-path-variable
category: laptrinhspring
tags: [spring-web]
summery: Request Param và PathVariable
image: /images/blog/spring.png
featureImage: /images/post/javacore/feature_request.jpg
description : Phân biệt Request Param và Path Variable . Hiểu được request param là gì?, hiểu được path variable là gì? Hướng dẫn cách sử dụng Request Parame và Path Variable trong lập trình spring. Các kết hợp cả 2 cách vào trong lập trình.
youtubeId: z3ZlVvu1yUY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào bạn , chắc bạn đang phân vân <b>Request Param</b> và <b>Path Variable</b> có khác gì nhau không ? Khi nào dùng thì bài viết hôm nay
anh sẽ trình bày sự khác nhau đó .

<br>
# **1. Request Param**

Chúng ta sử dụng <b>Request Param</b> ở controller để lấy giá trị người dùng nhập trên trình duyệt. Ví dụ khi người dùng gõ vào đường link như sau để gửi 2 giá trị 10 và 20 lên server .

http://localhost:8080/springmvc/hello/101?param1=10&param2=20

Phía Controller ta sẽ dùng <b>@RequestParam</b> để bắt lại 2 giá trị 10 và 20 như sau :

{% highlight java linenos %}
public String getDetails(@RequestParam(value="param1", required=true) String param1, @RequestParam(value="param2", required=false) String param2){

}
{% endhighlight %}

- @RequestParam : chúng ta sử dụng annotation @RequestParam để khai báo là sẽ sử dụng nó để lấy các giá trị trên url
- Value="param1" : Chúng ta khai báo để lấy giá trị tên là "param1" trên trình duyệt. Như vậy ứng với giá trị số 10 trên trình duyệt sẽ gán vào giá trị String param1
- Value="param2" : Thì nó tương tự mục đích ở trên , chúng ta khai báo để lấy giá trị tên param2. Như vậy nó sẽ lấy giá trị 20 và gán vào biên String param2
- require = true : Thì chúng ta bắt buột là trên url phải có tham số param1

<br>
# **2. Path Variable**

Sử dụng <b>Path Variable</b> ở Controller để lấy giá trị người dùng nhập trên trình duyệt. Nhưng ở đây mình sẽ không dùng theo định dạng key và value như ?param1=10&param2=20. Mà thay vào đó chúng ta sẽ sử dụng định dạng khác là /param/10.

Ví dụ khi người dùng nhập vào url sau và muốn truyền 1234 lên Controller thì bên Controller ta sử lý như sau .
http://localhost:8080/MyApp/user/1234

{% highlight java linenos %}
@RequestMapping(value="/user/{userId}", method = RequestMethod.GET)
public List<Invoice> listUsersInvoices(
            @PathVariable("userId") int user) {
  ...
}
{% endhighlight %}

- @RequestMapping(value="/user/{userId}" : chúng ta khai báo định dạng là /user/{userId}. Như vậy nó sẽ map với trình duyệt có định dạnh là user/1234

- @PathVariable chúng ta sẽ lấy số 1234 từ trình duyệt và gắn vào biên int user.

<br>
# **3. Kết hợp cả 2 trong 1 request**

Về mặt kỷ thuật chúng ta có thể sử dụng cả 2 phương pháp PathVariable và RequestParam trong một Controller để lấy giá trị từ url như sau.

http://localhost:8080/MyApp/user/1234/invoices?date=12-05-2013

{% highlight java linenos %}
@RequestMapping(value="/user/{userId}/invoices", method = RequestMethod.GET)
public List<Invoice> listUsersInvoices(
            @PathVariable("userId") int user,
            @RequestParam(value = "date", required = false) Date dateOrNull) {

}
{% endhighlight %}

Trong đó PathVariable sẽ sử dụng định dạng là /user/{userId}. Trong khi đó @RequestParam sẽ sử dụng định dạng key và value date (key) =12-05-2013 (value).
<br>
# **4. Kết luận**

Cả 2 cách trên đều thực hiện chung một nhiệm vụ là lấy các tham số từ người dùng truyền lên. Bạn sử dụng cái nào cũng làm được
mục đích của mình . Tuy nhiên tuỳ vào thiết kế của một hệ thống mà lựa chọn Request Param hoặc  Path Variable để sử dụng mới đem lại
hiệu quả cao được . Lấy ví dụ mình viết Restfull Web Service thì chắc chắn mình phải dùng Path Variable . Còn thường Request Param khi ta chỉ muống
query data trên URL.

<br>
### Và bây giờ, hãy cùng xem code demo ở bên dưới để hiểu rõ hơn nhé .

{:refdef: style="text-align: center;"}
{% include youtubePlayer.html id=page.youtubeId %}
{: refdef}
