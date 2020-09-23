---
layout: course-javascript
title: Sử dụng Callback  
slug : javascript-callback
category: laptrinhjavascript
tags: [javascript]
summery: Callback   
image: /images/blog/feature_javascript.png
description : Giới thiệu về callback trong Javascrip, cách hoạt động của callback trong Javascript
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người về <b>callback</b> là như thế nào?

# **1. Callback là gì**

Khái niệm callback có nghĩa là ta truyền một function như một tham số đến một funtion khác.

Thông thường chúng ta thấy khi khai báo hàm có tham số ví dụ

{% highlight javascript  linenos %}

function getData(x, y) {
    
    // code logic tại đây
}

{% endhighlight %}

- Thì tham số truyền vào trong hàm getData là kiểu dữ liệu.

Còn đối với Callback là ta truyền vào một function chứ không phải kiểu dữ liệu như ví dụ dưới đây

# **2.Ví dụ về Callback**

{% highlight javascript  linenos %}

function getData(x, y, callback){  
    document.write(" The multiplication of the numbers " + x + " and " + y + " is: " + (x*y) + "<br><br>" );  
    callback();  
}  

function showData(){  
document.write(' This is the showData() method execute after the completion of getData() method.');  
}  
getData(20, 30, showData); 

{% endhighlight %}

- Ở ví dụ trên ta có 2 function: 
- Function đầu tiên là getData với 3 tham số là x,y và callback (callback này là ta truyền vào đây một function như một tham số thứ 3 trong ví dụ trên tham số thứ 3 là function tên showData)   
- Function thứ 2 có tên là showData function này được truyền vào như 1 tham số 
- Khi chương trình chạy đầu tiên nó sẽ gọi function getData(x,y,callback) lúc này nó sẽ in ra màn hình "The multiplication of the numbers". Sau khi in ra màn hình xong thì lúc này nó mới gọi hàm showData lúc này nó sẽ in tiếp ra màn hình là "This is the showData() method execute after the completion of getData() method."

Như vậy callback mình sử dụng như làm tuần tự các công việc một cách đồng bộ. Có nghĩa là khi làm xong việc thứ nhất thì chạy tiếp các công việc thứ 2 cho mình.

# **3.Ví dụ 2 về Callback**

{% highlight javascript  linenos %}

    <html>  
    <head>  
      
    </head>  
    <body>  
    <h1> Hello World :) :) </h1>  
    <h2> This is the javaTpoint.com </h2>  
    <script>  
    function showData(name, amt) {  
    alert(' Hello ' + name + '\n Your entered amount is ' + amt);  
    }  
      
    function getData(callback) {  
    var name = prompt(" Welcome to the javaTpoint.com \n What is your name?");  
    var amt = prompt(" Enter some amount...");  
    callback(name, amt);  
    }  
      
    getData(showData);  
    </script>  
    </body>  
      
    </html>  
{% endhighlight %}

Tóm lại chúng ta sử dụng callback khi chúng ta muốn các công việc được sử lý đồng bộ theo trình tự nhất định



