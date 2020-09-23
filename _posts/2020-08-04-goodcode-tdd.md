---
layout: course-goodcode
title: Hướng dẫn viết TDD trong lập trình java
slug : lap-trinh-tdd
category: craftmanship
tags: [goodcode]
summery: Lập trình TDD    
image: /images/blog/quality-code.png
description : Nắm được nguyên lý và áp dụng được TDD trong lập trình. Nắm được vòng đời của một TDD và hướng dẫn sử dụng viết TDD trong dự án thực tế
youtubeId: LdLvwsj5_Sk
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn, chắc hẳn bạn sẽ muốn biết <b>TDD</b> là lập trình như thế nào phải không nào ? Trong bài viết hôm nay a sẽ giới thiệu từng bước giúp chúng ta có thể lập trình TDD một cách hiệu quả nhất.

<br>
# **1. Lập trình theo bản năng**

Một thói quen phổ biến của lập trình viên là khi nhận được yêu cầu của khách hàng hay từ team leader của mình. Thì việc đầu tiên là nhảy vào code ngay, chỉ phán đoán sơ bộ chức năng rồi nhảy vào viết các controller, các nghiệp vụ, kết nối database lấy dữ liệu. Đây là cách lập trình theo thói quen và  vội vã trong lúc lập trình dẫn đến có nhiều bugs phát sinh sau khi chức năng code xong và chức năng chạy không đúng với yêu cầu của người dùng. Vậy có cách nào để code ý lỗi hơn hay không. Sau đây anh sẽ trình bày cách lập trình TDD giúp mình viết ra một đoạn code ít bug.

<br>
# **2. TDD là gì**

TDD là viết tắt của từ <b>Test-Driven-Developement</b> được phát triển bởi <b>Kent Bech</b> (một trong những lập trình viên có tiếng trên thế giới không những về coding và còn về qui trình, đây là một trong số lập trình viên mà anh yêu thích,ngoài ra các em có thể tìm kiếm thêm Uncle Bob là những người đã đem lại những đột phá trong nghề lập trình giúp các lập trình viên ngày nay trở nên giỏi hơn).

Khi ta thực hiện cách viết code kiểu TDD. Nó yêu cầu mình phải suy nghỉ, thiết kế các <b>testcase</b> trước khi nhảy vào viết code. Sau khi viết code test xong thì sau  đó mới viết code thực thi chương trình, chứ không giống như trường hợp anh nói ở trên là lập trình viên bay vào code liền. Chính vì bắt buộc lập trình viên phải suy nghỉ trước khi test nên mình có thể dự đoán được các trường hợp sẽ xảy ra với dòng code của mình. Sau khi viết code thực thi xong thì công đoạn tiếp theo là sẽ tìm cách refactor (chỉnh sửa) code đã có trở nên gọn hơn, dể đọc hơn.

<br>
# **3. Vòng đời TDD**

Đề bài anh đưa ra như sau. Viết một method tên cal có tham số là number như sau cal(String numbers). Khi người dùng truyền vào tham số là cal("3,5") thì trả về tổng là 8. Vậy chúng ta sẽ áp dung TDD như thế nào. Trước hết mình sẽ nhìn qua vòng đời của TDD.

{:refdef: style="text-align: center;"}
![TDD](/images/post/softwarecraftmanship/tdd.png){:class="img-responsive"}
{: refdef}

## Bước 1 - Viết Test
Như vậy thay vì nhảy vào code luôn thì anh sẽ tạo một class để test.

Trước hết ta có code Production như sau

{% highlight java linenos %}
public class Calculator {



    public int cal(String numbers) {
        
        return 0;
    }


}
{% endhighlight %}

Như vậy các em thấy ta có code thực thi ở trên nhưng trong hàm cal(String numbers) ta chỉ trả về 0. Chưa viết code thực thi gì cả. Tiếp đến ta tạo ra class để test phương thức cal trong class Calculator như sau.

{% highlight java linenos %}
class CalculatorTest {

    private Calculator calculator;
    @Test
    public void testPlus2Number() {

        String input = "2,3";
        int expectedResult = 5;
        int actualResult =  calculator.cal(input);
        assertEquals(expectedResult,actualResult);
    }
}
{% endhighlight %}

Như các em thấy ta tạo ra class CalculatorTest có hàm testPlu2Number thì đây chính là 1 <b>testcase</b>. Mình sẽ suy nghỉ là nếu mình nhập vào số 2,3 thì kết quả mình nhận được là số 5.

## Bước 2 - Test Fail.

Như các em thấy nếu mình chạy testcase ở trên chắc chắn sẽ bị fail bởi vì code Productionn (code thực thi) ở bước 1 mình chưa viết gì cả mình chỉ trả về số 0. Như vậy khi mình truyền vào 2,3 ở test case thì mình luôn nhận được số 0.

## Bước 3 - Viết code thực thi

Khi mà mình biết được mình mong muốn ở gì ở testcase thì bước tiếp theo mình sẽ viết code Production để có thể Pass được test case ban đầu.

{% highlight java linenos %}
public class Calculator {



    public int cal(String numbers) {
        
        String[] nums = numbers.split(",");
 
 	    sum = Integer.parseInt(nums[0]) + Integer.parseInt(nums[1]);
        return sum;
    }


}
{% endhighlight %}

## Bước 4 - Chạy lại testcase

Sau khi viết code thực thi xong. Việc tiếp theo là mình chạy lại cái testcase xem code Production của mình có chạy đúng như testcase mình mong muốn hay không. Nếu chạy sai mình phải sửa code Production lại. Nếu chạy đúng thì chuyển qua bước cuối cùng là bước refactor.

## Bước 5 - Refactor code

Sau khi đã pass hết các testcase công việc tiếp theo của mình là xem có thể viết code Production ngắn lại được không. Thay vì 50 dòng code có thể viết thành 20 dòng code không. Có cần chỉnh sửa biến để dể hiểu , dể bảo trì không.

# **4. Vòng đời TDD tiếp theo**

Sau khi trả qua 5 giai đoạn của vòng đời 1 TDD. Chúng ta tiếp tục thiết kế các testcase khác có thể xảy ra cho cộng 2 số. Ngoài trường hợp chạy đúng ở trên
Ví dụ như điều gì xảy ra khi người dùng nhập vào chuổi là 3 số như hàm testPlus3NumberReturnToLastValue() sau.

{% highlight java linenos %}
    @Test
    public void testPlus2Number() {

        String input = "2,3";
        int expectedResult = 5;
        int actualResult =  calculator.cal(input);
        assertEquals(expectedResult,actualResult);
    }

    @Test
    public void testPlus3NumberReturnToLastValue () {
        String input = "1,2,3";
        int expectedResult = 5;
        int actual = calculator.cal(input);
        assertEquals(expectedResult,actual);
    }

{% endhighlight %}

Ta lại tiếp tục vòng đời mới là viết code thực thi, chạy testcase để đảm bảo code thực thi luôn đúng, sau đó là refactor. 

# **5. Ưu điểm**

Theo kinh nghiệm của anh thì <b>ưu điểm của TDD</b> là :

- Nó bắt buộc người lập trình phải suy nghỉ các trường hợp sẽ xảy ra với code của mình trước khi bắt đầu viết code Production. Điều này giúp lập trình viên có thể dự đoán các vấn đề xảy ra trong lúc viết code

- Khi anh làm TDD thì code mình ít bugs hơn vì các trường hợp xảy ra mình có thể dự đoán trước. Trong thực tế khi anh code một chức năng gì, anh thường chạy qua bên Tester (đội kiểm thử phần mềm của công ty) để hỏi xem trong method anh sắp code có những testcase nào có thể xảy ra. Vì Tester sẽ có nhiều kinh nghiệm dự đoán lỗi hơn mình. Nên việc tham khảo ý kiến tester trước khi code giúp code anh ít lỗi hơn.

- Có thể một tháng , một năm sau code của anh viết ở trên sẽ được bảo trì , và thêm các tính năng mới trong đó. Nếu không có các testcase mà anh viết thì có thể người đi sau sẽ code ra một cái nghiệp mới nhưng sẽ sai về mặt nghiệp vụ củ. Như vậy để tránh tình trạng sửa code mà nó chỉ chạy đúng tính năng mới còn tính năng củ trong method không đúng thì mình có các testcase để kiểm tra lại tổng thể cái code mới viết ra có chạy đúng hay không.

<br>
### Để hiểu rõ hơn các làm TDD các em xem video sau nhé.



{% include youtubePlayer.html id=page.youtubeId %}
