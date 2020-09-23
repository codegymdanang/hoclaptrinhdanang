---
layout: course-spring-web
title: Sử dụng Restful
slug : restful
category: laptrinhspring
tags: [spring-web]
summery: Restful
image: /images/blog/spring.png
featureImage: /images/post/javacore/feature_webservice.png
description : Sử dụng restful webservice trong lập trình. Hiểu cơ chế hoạt động của restfull webservice thông qua các  ví dụ thực tế. Phân biệt được sự khác nhau của website và webservice và khi nào thì mình dùng webservice trong lập trình java.
youtubeId: WNfuVJptPnQ
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em ,chủ để hôm nay chúng ta sẽ tìm hiểu về <b>Restful webservice</b>  là gì ?


<br>
# **1. Website là gì ?**

Trước tiên chúng ta sẽ tìm hiểu <b>webstie</b> là gì? Anh ví dụ khi mọi người nhập vào đường link https://lazada.com  mình sẽ nhận được website như sau:

{:refdef: style="text-align: center;"}
![Lazada](/images/post/spring/lazada.png){:class="img-responsive"}
{: refdef}

Để thấy được trang <b>web</b> lazada với đầy đủ nội dung và hình ảnh như vậy thì mình phải trải qua các bước sau

- Client (website) gửi một yêu cầu (request) lên con server. Trong trường hợp này người dùng gõ vào trình duyệt là https://lazada.com và yêu cầu server sẽ trả về website bao gồm html,css,ảnh, và dữ liệu)  

- Khi server nhận được request từ phía client . Nó sẽ chuẩn bị resource (trong trường hợp này là html và dữ liệu ) đúng như yêu cầu client. Sau khi client nhận được resouce (html,css,js,data) thì lúc đó hiển thị lên cho người dùng thấy được trang home hoàn chỉnh.

- Đây chính là luồng đi của ứng dụng website . Client yêu cầu (request) server trả về một resouce mà mình mong muốn. Resource ở đây có thể là html , một cái ảnh hay một cái file.

<br>
# **2. Webservice là gì ?**

Cũng là ví dụ trên nhưng giờ người dùng (client) không dùng <b>website</b> nữa mà thay vào đó là ứng dụng trên điện thoại di động. Người dùng mở điện thoại và bật ứng dụng lazada lên. Như các em thấy trên ứng dụng di động chúng ta không thể trả về <b>html,css</b> được. Mà ta chỉ muốn server trả về <b>dữ liệu</b> (data) sau đó mình sẽ dùng ngôn ngữ lập trình của mobile để hiển thị dữ liệu.

Như vậy chúng ta không thể áp dụng nguyên lý của <b>website</b> vào đây. Mà thay vào đó chúng ta sẽ sử dụng một công nghệ gọi là <b>webservice</b>. Ở đây chúng ta yêu cầu server trả về <b>dữ liệu (data)</b> thôi  và sau đó tuỳ thuộc vào <b>frontend</b> đang dùng ngôn ngữ gì mà mình hiển thị dư liệu lên.

Thông thường server sẽ trả dữ liệu dựa trên 2 dạng là <b>XML</b> và <b>JSON</b> về cho client.

Đây là dạng dữ liệu XML
{% highlight xml  linenos %}
<?xml version="1.0"?>
<user>
 <name>Smith</name>
</user>
{% endhighlight %}

Đây là dạng JSON
{% highlight java  linenos %}
{
 "date": "2016-08-27",
 "location": "Chicago",
 "info": "Hot"
}
{% endhighlight %}

<br>
# **3. Restfull webservice là gì?**

<b>REST</b> là viết tắt của từ (REpresentational State Transfer ). Anh lấy ví dụ về lazada . Khi mình vào click vô xem chi tiết của một sản phẩm thì mình sẽ thấy thông tin của nó gồm mô tả , giá , số lượng. Như vậy khi client gửi request (yêu cầu) lên server để lấy thông tin về sản phẩm. Ví dụ backend là mình viết bằng Spring (java) thì lúc đó Controller sẽ gọi các services để lấy dữ liệu và kết quả của các service trả về là một đối tượng Product (có thuộc tính mô tả, giá , số lượng). Tuy nhiên ta sẽ không trả về đối tượng Product cho client ngay mà đối tượng Product đó sẽ được chuyển đổi thành dạng Json hoặc XML rồi gửi về cho client.

Sự chuyển đổi đó gọi là  REpresentational State Transfer. Representational có nghĩa là hiển thị kiểu json hay xml. State có nghĩa là trạng thái của dữ liệu từ Object Java mình chuyển sang trạng thái khác để truyền đi. Transfer nghĩa là động tác chuyển đổi dữ liệu Object sang kiểu định dạng mới là json hay xml . Nói tóm lại ta chuyển đổi trạng thái dữ liệu từ object sang kiểu json hay xml để client có thể nhận được data.

<b>Restfull Webservice</b>  là một dạng webservice viết theo chuẩn REST. REST quy định các quy tắc để bạn làm ra một webservice . Nó chú trọng vào việc lấy resouce (tài nguyên) như là data, image , files từ server trả về client thông qua protocal http.

Bất kỳ một ứng dụng nào cũng thực hiện thao tác CRUD (tạo,đọc,sửa,xoá) dữ liệu. Rest đặt ra một quy tắc mà các lập trình viên muốn xát định rõ ý định của mình thông qua các phương thức http.

- Khi lấy dữ liệu, đọc dữ liệu từ server thì phương thức request mình dụng là <b>Get</b>
- Khi tạo mới một resource thì  phương thức  request là <b>Post</b>
- Khi cập nhật giá trị thì   phương thức  request là <b>Update</b>
- Khi xoá một giá trị thì  phương thức  request là <b>Delete</b>

Ví dụ sau là một Restfull của Spring . Ta định nghĩa các <b>@GetMapping</b> tương ứng với method request là GET.
<b>@PostMapping</b> ứng với request là http Post. <b>@DeleteMapping</b> ứng với request có http là DELETE. Và <b>@PutMapping</b> ứng với request Update.

{% highlight java  linenos %}
@RestController
@RequestMapping("/api/books")
public class BookController {

    @Autowired
    private BookRepository bookRepository;

    @GetMapping
    public Iterable findAll() {
        return bookRepository.findAll();
    }

    @GetMapping("/title/{bookTitle}")
    public List<Book> findByTitle(@PathVariable String bookTitle) {
        return bookRepository.findByTitle(bookTitle);
    }

/*    @GetMapping("/{id}")
    public Book findOne(@PathVariable Long id) {
       Book book1 = new Book();
       return book1;
    }*/


    @GetMapping("/{id}")
    public Book findOne(@PathVariable Long id) {
        return bookRepository.findById(id).orElseThrow(BookNotFoundException::new);
    }



    @PostMapping
    @ResponseStatus(HttpStatus.CREATED)
    public Book create(@RequestBody Book book) {
        Book books = bookRepository.save(book);
        return books;
    }

    @DeleteMapping("/{id}")
    public void delete(@PathVariable Long id) {
        bookRepository.findById(id)
                .orElseThrow(BookNotFoundException::new);
        bookRepository.deleteById(id);
    }

    @PutMapping("/{id}")
    public Book updateBook(@RequestBody Book book, @PathVariable Long id) {
        if (book.getId() != id) {
            throw new BookNotFoundException();
        }
        bookRepository.findById(id)
                .orElseThrow(BookNotFoundException::new);
        return bookRepository.save(book);
    }
{% endhighlight %}

Ở ví dụ trên nếu phương thức <b>request</b> là Post sẽ gọi hàm create. Nếu phương thức request là Delete sẽ gọi hàm delete. Như vậy Rest quy định rất rõ ràng  từng phương thức tương ứng với hành động CRUD

<br>
# **4. Kết luận?**

Ngày nay thì đa số các ứng dụng webservice đều là Restfull cả . Vì nó có nhiều ưu điểm hơn các loại khác như Web Service dựa trên SOAP và WSDL. Đồng thời REST để bảo trì và mở rộng.
