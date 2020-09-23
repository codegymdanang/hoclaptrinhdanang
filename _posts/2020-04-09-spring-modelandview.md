---
layout: course-spring-web
title: Sử dụng Model ModelMap ModelView  
slug : model-modlemap-modelview
category: laptrinhspring
tags: [spring-web]
summery: Model ModelMap ModelView
image: /images/blog/spring.png
featureImage: /images/post/javacore/feature_modelandview.png
description : Sử dụng Model ModelMap ModelView trong lập trình Springg. Hiểu model là gì  trong Spring . ModelMap là gì , Map là gì , ModelAndView là gì trong Spring. Phân biệt sự khác nhau giữ Model ModelMap Map và ModelAndView trong học lập trình Spring.
youtubeId: WzRjQjubR6o
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**
Chào bạn, trong bài viết hôm nay anh sẽ giới thiệu cho các bạn phân biệt <b>Model</b>, <b>ModelMap</b>, <b>Map</b> và <b>ModeAndView</b>. 

<br>
# **1. Model là gì**

Chúng ta sử dụng Interface <b>Model</b> để truyền dữ liệu từ Controller sang View để hiển thị .
Spring cho phép chúng ta sử dụng Model như là một tham số trong method của Controller nên chúng ta dể dàng lấy , chỉnh sử dữ liệu
để truyền qua cho View.

Như vậy model như là một cầu nối dữ liệu giữa Controller và View. Tầng view có nhiệm vụ hiển thị dữ liệu ra cho người dùng và dữ liệu đó được controller truyền sang cho view. View sẽ kết hợp dữ liệu thô từ controller với <b>HTML,CSS,JS</b> để cho ra một trang web đẹp và hoàn chỉnh.

{% highlight java linenos %}

@Controller
public class GreetingController {

    @RequestMapping(path = "/getWithModel", method = RequestMethod.GET)
    public String getWithModel(@RequestParam("name") String name, Model model) {
        Greeting greeting = new Greeting(name);
        model.addAttribute("greeting", greeting);

        return "greet";
    }
}
{% endhighlight %}

Trong method getWithModel chúng ta có tham số là Model model. Chúng ta sử dụng nó bằng các thêm các giá trị mà chúng ta mong muốn tầng View sẽ sử dụng. Model hỗ trợ ta phương thức <b>addAttribute</b>, anh ví dụ như chúng ta muốn truyền đối tượng greeting từ controller qua cho view thì ta thêm như sau : model.addAttribute("greeting", greeting). Trong đó tham số đầu tiên là tên (greeting) nhờ có tên này mà mình có thể lấy ra đối tượng greeting bên view. Tham số thứ 2 là đối tượng mình mong muốn truyền qua cho View

Như vây tầng view chúng ta có thể lấy data truyền từ model như sau

{% highlight html  linenos %}
<!DOCTYPE html>
<html>
    <body>
        Hello <span th:text="${greeting.name}"/>!
    </body>
</html>
{% endhighlight %}
<br>


Chúng ta sử dụng <b>${greeting.name}</b> để lấy giá trị bên controller gửi qua. Đây là cách đọc giá trị từ controller qua view bằng kỷ thuật Themeleaf sử dụng cú pháp ${} . Ngoài Themeleaf chúng ta còn nhiều kỷ thuật khác như Velocity, Jstl ect.


<br>
# **2. ModelMap là gì**

<b>ModelMap</b> cũng tương tư như <b>Model</b>. Chúng ta có thể sử dụng <b>ModelMap</b> như một tham số trong method của Controller.

{% highlight java  linenos %}
@RequestMapping(path = "/getWithModelMap", method = RequestMethod.GET)
public String getWithModelMap(@RequestParam("name") String name, ModelMap modelMap) {
    Greeting greeting = new Greeting(name);
    modelMap.addAttribute("greeting", greeting);
    return "greet";
}

{% endhighlight %}

Trong phương thức getWithModelMap ta có thêm tham số là <b>ModelMap</b> modelMap thay vì Model

<br>
# **3. Map**

Map cũng tương tự như <b>Model</b>. Chúng ta có thể sử dụng Map như một tham số trong method của Controller.

{% highlight java  linenos %}
@RequestMapping(path = "/getWithMap", method = RequestMethod.GET)
public String getWithMap(@RequestParam("name") String name, Map<String, Object> model) {
    Greeting greeting = new Greeting(name);
    model.put("greeting", greeting);
    return "greet";

}
{% endhighlight %}

Trong phương thức getWithModelMap ta có thêm tham số là Map gồm có key và value và ta sử dụng phương thức put thay vì addAttribute như <b>model</b> và <b>modelmap</b>

<br>
# **4. ModelAndView**

Là sự kết hợp của 2 khía cạnh truyền dữ liệu và view. Như ta thấy ở ví dụ trên ta dùng 2 dòng code.

1. model.put("greeting", greeting); gán dữ liệu greeting cho biến greeting.

2. return "greet" ; trả về trang view là greet.html.
Chúng ta sử  ModelAndView("greet", modelMap) để thực hiện việc , trả về trang greet.html và mode 1 lần .

{% highlight java  linenos %}
@RequestMapping(path = "/get", method = RequestMethod.GET)
public ModelAndView get(@RequestParam("name") String name) {
    Map<String, Object> modelMap = new HashMap<>();
    Greeting greeting = new Greeting(name);
    modelMap.put("greeting", greeting);

    return new ModelAndView("greet", modelMap);
{% endhighlight %}

<br>
# **5. Sự khác nhau giữa các model**

1. Model là một interface trong khi đó ModelMap là một Class.
2. Model là một  interface nó chứa đựng 4 phương thức addAttribute và một phương thức  merAttribute .
3. ModelMap cài đặt lớp  Map interface. Nên nó thêm các phương thức của Map.
4. ModelAndView là sự kết hợp của 2 mục đích  ModelMap and View . Nó cho phép controller trả về 1 giá trị bao gồm Model và View .  

<br>
# **6. Và bây giờ, hãy cùng xem code demo ở bên dưới để hiểu rõ hơn nhé**

{:refdef: style="text-align: center;"}
{% include youtubePlayer.html id=page.youtubeId %}
{: refdef}
