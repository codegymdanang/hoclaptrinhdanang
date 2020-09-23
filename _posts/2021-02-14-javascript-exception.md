---
layout: course-javascript
title: Ngoại lệ  
slug : javascript-exception
category: laptrinhjavascript
tags: [javascript]
summery: Ngoại lệ   
image: /images/blog/feature_javascript.png
description : Giới thiệu về ngoại lệ trong Javascrip, cách hoạt động của ngoại lệ trong Javascript
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>ngoại lệ</b>là như thế nào?

# **1. Ngoại lệ là gì**

Trong quá trình lập trình với Javascript sẽ có những lúc code mình không chạy như mình mong muốn và nó quăng ra lỗi làm cho chương trình mình dừng lại. Các lỗi đó mình gọi là ngoại lệ (Exception). Khi lập trình thì mình sẽ sử dụng các từ khoá try catch để mình bắt lại ngoại lệ xử lý để chương trình tiếp tục chạy

Có 3 loại ngoại lệ thường xảy ra khi mình lập trình javascript. Mình sẽ gặp lỗi cú pháp khi mì gõ sai cú pháp (Syntax Error) thì sẽ bị gặp lỗi. Hoặc trong quá trình chương trình mình chạy gặp lỗi thì gọi là Runtime Error. Hoặc mình bị sai về logic.

# **2. Đối tượng Error**

Khi chương trình chạy bị lỗi nó sẽ ném ra đối tượng là Error cho mình. Trong đối tượng Error có 2 thuộc tính là name (tên của lỗi) và message (nội dung của lỗi). Chúng ta sử dụng try catch để bắt lại đối tượng Error này. Tuỳ vào message (nội dung) của lỗi là gì mà chúng ta sử lý.

# **3. Sử dụng khối lệnh try-catch để bắt ngoại lệ**

- Cú pháp


{% highlight javascript  linenos %}

<script>

    try{  
        code chương trình; 
    } //code to be written.  
    catch(error){  
       bắt lỗi và xử lý lỗi nếu có khi chạy code chương trình; 
    } // code for handling the error

</script>

{% endhighlight %}

- Ví dụ

{% highlight javascript  linenos %}

<script>
try{
    var a= ["34","32","5","31","24","44","67"]; //a is an array
    document.write(a);    // displays elements of a
    document.write(b); //b is undefined but still trying to fetch its value. Thus catch block will be invoked
}catch(e){
    alert("There is error which shows "+e.message); //Handling error
}
</script>
{% endhighlight %}

- Chúng ta sẽ dụng e.message để lấy thông báo lỗi (e là đại diện cho Error)

# **4. Sử dụng Throw ném ngoại lệ**

Sẽ có những trường hợp trong function của mình muốn ném ra một ngoại lệ để các function khác khi gọi nó có thể bắt ngoại lệ và xử lý tiếp. Để function ném ra ngoại lệ thì ta dùng từ khoá Throw

- Cú pháp

{% highlight javascript  linenos %}

    try{  
        throw exception; // user can define their own exception  
    }catch(error){  
        expression; 
    }  // code for handling exception.
{% endhighlight %}

- Ví dụ

{% highlight javascript  linenos %}

<script>  
try {  
   throw new Error('This is the throw keyword'); //user-defined throw statement.  
}  
catch (e) {  
  document.write(e.message); // This will generate an error message  
}  
</script>

{% endhighlight %}

# **5. Khối lệnh finally**

Khối lệnh finally là trường hợp đặt biệt ta có thể dùng hoặc không dùng chung với try catch. Khối lệnh finally luôn luôn chạy các dòng code trong nó dù ngoại lệ có được ném ra hay không.

- Cú pháp

{% highlight javascript  linenos %}

<script>  

    try{  
        expression;  
    }  
    catch(error){  
         expression;  
    }  
    finally{  
        expression; 
    } //Executable code  
</script>

{% endhighlight %}

- Ví dụ 

{% highlight javascript  linenos %}
<script>  
    try{  
        var a=2;  
        if(a==2)  
        document.write("ok");  
    } catch(Error){  
        document.write("Error found"+e.message);  
    }  finally{  
        document.write("Value of a is 2 ");  
    }  
</script>

{% endhighlight %}










