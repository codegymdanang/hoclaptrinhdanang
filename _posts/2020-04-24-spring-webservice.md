---
layout: course-spring-web
title: Webservice
slug : webservice
category: laptrinhspring
tags: [spring-web]
summery: Webservice
image: /images/blog/spring.png
featureImage: /images/post/javacore/feature_webservice.png
description : webservice là gì trong học lập trình. Hiểu được webservice thông qua các ví dụ thực tế. Phân biệt được các loại webservice hiện nay gồm SOAP và Restful webservice trong lập trình java.
youtubeId: WNfuVJptPnQ
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em ,chủ để hôm nay chúng ta sẽ tìm hiểu về <b>webservice</b> là gì ?

<br>
# **1. Webservice là gì ?**

<b>Webservice</b> là tập hợp các tiêu chuẩn và giao thức được sử dụng để <b>trao đổi dữ liệu</b> giữa các ứng dụng hoặc các hệ thống khác nhau.

Anh lấy ví dụ như sau : Anh muốn phát triển một ví điện tử  (dạng Momo) có tên là Le-ebaking. Ứng dung Le-ebaking có thể kết nối với ngân hàng HSBC , Techcombank , Vietcombank. Người dùng có thể chuyển tiền từ hệ thống Techcombank sang Vietcombank thông qua ứng dụng Le-ebaking.

Trong đó HSBC được viết bằng ngôn ngữ <b>PHP</b> chạy trên Server Window, HSBC viết bằng ngôn ngữ <b>Java</b> chạy trên Ubuntu và Techcombank viết bằng ngôn ngữ <b>Ruby</b> và chạy trên nền MacOS. Như vậy ta thấy 3 ngân hàng sử dụng 3 loại ngôn ngữ lập trình khác nhau và triển khai trên 3 nền tảng OS khác nhau. Vậy làm sao các ứng dụng đó có thể trao đổi dữ liệu với nhau được. May mắn cho chúng ta đã có Webservice,nó  giúp chúng ta có thể trao đổi dữ liệu từ các ứng dung , ngôn ngữ , OS khác nhau có thể nói chuyện được với nhau.

Trong thực tế khi anh làm ứng dụng payment thì dự án của anh cũng gọi các <b>webservice</b> của các ngân hàng khác. Anh không quan tâm webservice của ngân hàng đó viết bằng ngôn ngữ gì, chạy trên nền tảng gì. Ngân hàng mà hợp tác với anh sẽ cung cấp cho anh một <b>webservice</b> dựa vào đặt tả webservice thì mình sẽ gọi lên ngân hàng đó và lấy kết quả về cho ứng dụng của mình. Sau đó mình làm gì tiếp với dữ liệu là phụ thuộc vô nghiệp vụ của ứng dụng mình.

<br>
# **2. Các loại webservice**

Có 2 loại webservice chính đó là

- SOAP Webservice
- Restful Webservice

<br>
# **3. SOAP webservice là gì**

Anh sẽ lấy ví dụ ở ứng dụng Le-ebaking. Bây giờ người dùng của ứng dụng Le-ebanking có 3 tài khoản của 3 ngân hàng là Techcombank , HSBC và Vietcombank trong ví điện tử của mình. Người dùng muốn xem số dư tài khoản của ứng dụng Techcombank còn bao nhiêu tiền. Lúc đó ứng dụng Le-ebanking sẽ kết nối với ngân hàng Techcombank và thực hiện hành động lấy kết  số dư của khách hàng ở ngân hàng Techcombank.

Để thực hiện được chức năng ở trên. Việc đầu tiên ngân hàng Techcombank sẽ cung cấp cho anh đường link của webservice ví dụ là http://www.techcombank.com/getBalance. Dựa vào đường link này anh sẽ gọi webservice của Techcombank và anh sẽ nhận được kết quả là một file XML . Tiếp đến anh sẽ tìm trong file xml đó có trường nào có tên là balance không ? Nếu có anh sẽ lấy được giá trị của nó. Sau đó anh sẽ xử lý giá trị đó và trả về kết quả cho người dùng.

Như vậy trong java code mình gọi webservice của Techcombank như sau

{% highlight java  linenos %}
@Endpoint
public class TechcombankEndpoint {

    private static final String NAMESPACE_URI = "http://www.techcombank.com/getBalance";

    private TechcombankRepository techcombankRepository;

    @Autowired
    public TechcombankEndpoint(TechcombankRepository techcombankRepository) {
        this.techcombankRepository = techcombankRepository;
    }

    @PayloadRoot(namespace = NAMESPACE_URI, localPart = "getBalanceRequest")
    @ResponsePayload
    public GetBalanceResponse getBalance(@RequestPayload GetBalanceRequest request) {
        GetBalanceResponse response = new GetBalanceResponse();
        response.setBalance(techcombankRepository.findBalance(request.getName()));
        return response;
    }
}  
{% endhighlight %}

Khi mình gọi lên Techcombank service thì mình sẽ nhận lại kết quả (response) như sau

{% highlight java  linenos %}
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
<SOAP-ENV:Header/>
<SOAP-ENV:Body>
    <ns2:getBalanceResponse xmlns:ns2="http://www.techcombank.com/getBalance">
        <ns2:country>
            <ns2:balance>1000</ns2:balance>
            <ns2:currency> USD </ns2:currency>
        </ns2:country>
    </ns2:getBalanceResponse>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
{% endhighlight %}

Như các em thấy mình có thẻ <b>xml</b> '<ns2:balance>1000</ns2:balance>' với giá trị và 1000. Như vậy ứng dụng Le-ebanking sẽ lấy giá trị 1000 từ kết quả trả về, sau đó mình trả lại kết quả này cho người dùng

<br>
# **4. Restful webservice là gì**

Anh sẽ lấy ví dụ ở ứng dụng Le-ebaking. Bây giờ người dùng của ứng dụng Le-ebanking có 3 tài khoản của 3 ngân hàng là Techcombank , HSBC và Vietcombank trong ví điện tử của mình. Người dùng muốn xem số dư tài khoản của ứng dụng HSBC còn bao nhiêu tiền. Lúc đó ứng dụng Le-ebanking sẽ kết nối với ngân hàng HSBC và thực hiện hành động lấy kết  số dư của khách hàng ở ngân hàng HSBC.

Để thực hiện được chức năng ở trên. Việc đầu tiên ngân hàng HSBC sẽ cung cấp cho anh đường link của webservice ví dụ là http://www.hsbc.com/getBalance. Dựa vào đường link này anh sẽ gọi webservice của HSBC và anh sẽ nhận được kết quả là một file JSON  . Tiếp đến anh sẽ tìm trong file JSON đó có trường nào có tên là balance không ? Nếu có anh sẽ lấy được giá trị của nó. Sau đó anh sẽ xử lý giá trị đó và trả về kết quả cho người dùng.

Như vậy trong java code mình gọi webservice của HSBC như sau

{% highlight java  linenos %}
@RestController
public class EmployeeController {

    @GetMapping("/balance")
    public List<Employee> balance(id) {
      final String uri = "http://www.hsbc.com/getBalance";
      RestTemplate restTemplate = new RestTemplate();
      Employee employeeResponse = restTemplate.getForObject(uri, Employee.class);
      return employeeResponse ;
    }
  }
{% endhighlight %}

Kết quả mình nhận được sẽ là một file <b>json</b>. Trong đó có giá trị balance là 1000. Sau đó ta sử lý và gửi giá trị balance về cho người dùng app.

{% highlight json  linenos %}
{
  "id": 1,
  "balance": 1000,
}
{% endhighlight %}

<br>
# **5. Kết luận**

Ngày nay thì mình sử dung Restful webservice nhiều hơn SOAP webservice . Vì ưu điểm của Restful là truyền dữ liệu đi nhanh hơn, ít tốn băng thông.

Các em muốn biết Restful là gì thì đọc bài này nhé
[Restfull là gì](https://levunguyen.com/laptrinhspring/2020/05/10/restful/)
