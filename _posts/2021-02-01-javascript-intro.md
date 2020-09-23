---
layout: course-javascript
title: Giới thiệu về Javascript  
slug : javascript-introduction
category: laptrinhjavascript
tags: [javascript]
summery: Javascript là gì   
image: /images/blog/feature_javascript.png
description : Giới thiệu về Javascrip, cách hoạt động của Javascript
youtubeId: Ex3glZTCvlY
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn,hôm nay anh sẽ hướng dẫn mọi người chuẩn bị học <b>Javascript</b>là như thế nào?

# **1. Javascript là gì**

Anh lấy ví dụ như ứng dụng facebook chúng ta hay sử dụng. Khi vào facebook mình sẽ thấy giao diện facebook gồm hình ảnh và các bài post của những người bạn. Cái mà làm cho mình thấy giao diện như vậy được thì người ta sử dụng HTML, nó được dùng để xây dựng các giao diện. Tuy nhiên nếu có giao diện không thôi thì chưa đủ để làm một ứng dụng web. Có khi nào các em thắc mắc khi mình gõ một đoạn comment lên bài post của bạn mình rồi bấm enter thì chuyện gì xảy ra không? và làm sao mình gửi những những đoạn text đó lên để server facebook có thể lưu lại và lần sau mình vào thì mình vẫn thấy đoạn comment của mình. Vậy làm cách nào từ giao diện mình gửi đoạn văn bản lên server được. Thì đó chính là công dụng đầu tiên của JavaScript. Mình dùng nó như một cầu nối ở giữa giao diện(HTML) và Server (xử lý comment). Nhờ có Javascript mà mình có thể gửi các dữ liệu ở web lên cho server. Tiếp đến các em có hay chú ý những trang web có những animation (hiệu ứng) như bay, nhảy các kiểu thì mình dùng Javascript để làm các hiệu ứng  đó. Hoặc chúng ta sử dụng Javascript để kiểm tra dữ liệu người dùng nhập vào có đúng yêu cầu hay không. Anh ví dụ như yêu cầu người dùng nhập vào phải là số trong ô số điện thoại hoặc yêu cầu nhập đúng định dạng email bắt buộc phải có dấu @.

Javascript là ngôn ngữ kịch bản nó được chạy trong trình duyệt của người dùng. Sử dụng Javascript để thao tác với các thành phần của web như text, button, image , etc.

# **2. Cài đặt môi trường cho Javascript**

Để học và viết được ngôn ngữ Javascript chúng ta cần cài đặt trình duyệt. Có thể dùng Internet Exploer, Chrome, FireFox, Coccoc. Đây là những trình duyệt giúp chúng ta thấy được kết quả khi chạy các dòng code javascript. Anh thì hay dùng Chrome và FireFox để chạy Javascript

Các công cụ dùng để lập trình Javascript thì chúng ta có thể dụng Webstorm, Visual Studio là nhiều. Anh thì đang dùng Webstorm nhưng bản này là bản trả tiền, mọi người có thể sài Visual Studio bản này miễn phí

Ngoài ra chúng ta có thể lập trình Javascript online. Các tool như plnkr.co, jsfiddle.net hoặc jsbin.com đều được cả

# **3. Thẻ Javascript**

Tất cả code JS được viết ở trong thẻ < script > nếu ta đặt những đoạn code của mình trong file html.

Cú pháp như sau

{% highlight javascript  linenos %}

<script>
            
    //Viết code javascript tại đây
            
</script>


{% endhighlight %}

Nếu như ta không đặt file JS ở trong file html thì ta hoàn toàn có thể tạo một file JS ở ngoài sau đó trong file html chúng ta link nó vào như sau.

Ví dụ anh có file main.js

{% highlight html  linenos %}

<html>
<head>
    <meta name="viewport" content="width=device-width" />
    <title>JavaScript Demo</title>   
    <script src="/main.js"/>  
</head>
<body>
</body>

{% endhighlight %}

# **4. Đặt file JS ở đâu trong html**

Chúng ta thường đặt file JS ở cuối cùng của thẻ body. Vì khi trang web được load lên nó sẽ load từ trên xuống dưới. Trong trường hợp ta đặt file JS ở trên thì sẽ gây ra việc trình duyệt sẽ phải đọc file js sau đó mới render ra giao diện nó gây ra tình trạnh trang web load lên chậm. Nếu đặt ở cuối thì các thành phần trang web được load lên trước sau đó mới load JS như vậy người dùng sẽ thấy nhanh hơn.

{% highlight html  linenos %}

<!DOCTYPE html>

<html>
<head>
    <meta name="viewport" content="width=device-width" />
    <title>JavaScript Demo</title>
   
</head>
<body>
    <h1> JavaScript Tutorials</h1>
    <p>This is JavaScript sample.</p>
   
   
    <script src="/main.js"></<script>
</body>
</html>

{% endhighlight %}

# **5. Hiển thị Popup Message**

Javascript xây dựng sẳn môt số function (chức năng) có sẳn. Trong bài hôm nay chúng ta sẽ học một chức năng là hiển thị popup. 

- Ví dụ sử dụng Alert Box để hiển thị popup alert

{% highlight javascript  linenos %}

<script>
	
	alert("This is alert box!");  // display string message

</script>

{% endhighlight %}

- Ví dụ như Comfirm Box. Popup hiện thị 2 nút Ok và Cancel

{% highlight javascript  linenos %}

<script>

if (confirm("Do you want to save changes?") == true) {
    userPreference = "Data saved successfully!";
} else {
    userPreference = "Save Cancelled!";
}
</script>

{% endhighlight %}

- Ví dụ Promt Box, yêu cầu người dùng nhận vào dữ liệu

{% highlight javascript  linenos %}

<script>

var tenure = prompt("Please enter preferred tenure in years", "15");
    
if (tenure != null) {
    alert("You have entered " + tenure + " years" );
}
</script>

{% endhighlight %}
























