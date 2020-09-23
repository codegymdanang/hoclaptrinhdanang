---
layout: blog
title: Sử dụng Jenkins trong dự án
slug : jenkins
category: devops
tags: [cicd]
summery: Jenkins tự động CI-CD   
image: /images/blog/cicd.png
description : Sử dụng Jenkins trong dự án java. Hiểu CI CD là gì ?. Những khó khăn khi không áp dụng ci cd trong các dự án. Hướng dẫn triển khai dự án java kết hợp ci cd trên công cụ Jenkins.
youtubeId: nhWzKyz9H3s
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các bạn, bạn đang thắc mắc <b>CI/CD</b> là cái gì trong lập trình ? Nó được ứng dụng như thế nào trong phần mềm ? Sử dụng nó có mang lại
hiệu quả cao không? Và tại sao các công ty đều sử dụng nó. Hôm nay anh sẽ giới thiệu cho mọi người một tool tên là Jenkins mà các doanh
nghiệp hay dùng để làm CICD


# **1. CICD là gì**

CI là viết tắt của từ <b>Countinue Integration</b> nó có nghĩa là tự động tích hợp các modules các classes trong chương trình xem có chạy đúng chức năng hay không. Thông thường khi phát triển một phần mềm thì có rất nhiều modules tương tác với nhau để thực hiện một nhiệm vụ cụ thể. Nếu chạy riêng lẻ các module nó có thể chạy đúng nhưng khi tích hợp các module khác lại với nó thì có thể dẫn đến bugs. Chính vì vậy khi code xong một module mình phải chạy tích hợp để đảm bảo các chức năng chạy ok. Để làm được điều này nếu chạy bằng tay thông thường thì sẽ mất rất nhiều thời gian, chính vì vậy sử dụng tool để nó giúp mình làm đều này. Mỗi lần mình viết xong một đoạn code thì tool đó sẽ tự động chạy CI để tích hợp và mình có thể phát hiện ra bug nhanh và rất hiệu quả.

CD là viết tắt của <b>Countinue Deploy</b> nó có nghĩa là tự động triển khai code của mình lên con server được chỉ định. Trong lập trình sau khi viết xong một chức năng mình sẽ deploy (triển khai) nó lên con server để người dùng có thể sử dụng được. Nếu mình deploy bằng tay thì sẽ có những lúc sơ xuất dẫn đến chương trình chạy sai. Để tránh tình trạng deploy sản phẩm bằng tay do con người làm thì tool có thể giúp mình deploy chính xát. Nếu lần đầu đã đúng thì những lần tiếp theo vẫn chạy đúng vì nó được deploy theo cách mình đã lập trình sẳn. Còn nếu là con người thì có những lúc mình sẽ làm thiếu một số bước.

# **2. Làm việc không có CICD**

Cách đây 8 năm khi anh làm viêc trong team phát triển sản phẩm cho thị trường siêu thị bên Mỹ. Thì đây là vòng đời từ lúc code tới việc test và triển khai sản phẩm không dùng CICD

- Nguyen finished a task
- Nguyen asked Devop to deploy
- Devop pulled source code from repository
- Devop built it on Dev server
- Devop announced Nguyen the process is done
- Nguyen asked Tester to test
- Tester tested a task and reported the task is ok or not
- If not Nguyen fixed it 
- Nguyen repeated the action to ask the Devop guy to pull code and deploy
- Nguyen asked Tester test it again
- Devop merged code from dev branch to test branch
- Devop deployed the code on Test server
- Devop announced tester to do full test on Test server
- Tester retest all test cases

Như các em thấy tất cả các khâu lập trình đều làm bằng tay , bằng trao đổi và anh gặp các vấn đề sau :

- Nguyen finished a task
- Nguyen asked Devop to deploy   -> Repeat action | lack of notification
- Devop pulled source code from repository -> Repeat action
- Devop built it on Dev server -> Repeat action
- Devop announced Nguyen the process is done -> notification
- Nguyen ask Tester to test -> notification
- Tester reported the task is ok or not -> only test business how about the quality of code
- If not Nguyen fixed it -> Waiting too long to know it has a bugs, feedback is late
- Nguyen repeated the action to ask the Devop guy to pull code -> Repeat action
- Nguyen ask Tester test it again -> notification
- Devop merged code from dev branch to test branch -> Risky because 1 week of code need to merge. Maybe missing some people’s code
- Devop deployed the code on Test server -> Repeat
- Devop announced tester to do full test on Test server -> Notification
- Tester retest all test cases -> manually testing how about automation testing, daily reports, commit report

Như vậy anh tốn quá nhiều thời gian cho các công việc mà lập đi lập lại nhiều lần. Có quá nhiều thông báo cho đội tester và đội triển khai sản phẩm. Dẫn đến năng suất thấp, chức năng có nhiều bugs

# **3. Làm việc với CICD**

Chính vì các nhược điểm đã nêu ở trên nên sau này khi bắt đầu một dự án mới anh đều sử dụng tool để làm CICD. Tool thì có nhiều loại như <b>TravisCI</b>, <b>Jenkins</b>.
Cái mà anh hay dùng ở công ty là Jenkins.

- Vòng đời của CICD

{:refdef: style="text-align: center;"}
![TDD](/images/post/softwarecraftmanship/cicd.png){:class="img-responsive"}
{: refdef}

- Bước 1  	: Lập trình viên commit code lên github
- Bước 2	: Github sẽ trigger (gọi đến jenkins server). Cái này thì mình configure (xem video)
- Bước 3	: Jenkins sẽ bắt đầu chạy các jobs mà mình định nghĩa sẳn trong Jenkins như tự động tích hợp, tự động build dự án, tự động kiểm tra chất lượng
- Bước 4	: Sau khi jenkins đã chạy xong các công việc tích hợp thì mình sẽ cấu hình để jenkins đưa code lên server 

Vòng đời cứ tiếp tục diển ra mỗi khi có một lập trình viên nào commit code lên github. Như vậy mình tích hợp các module ngay tức thì. Cùng một lúc mình có thể triển khai source code lên nhiều con server khác nhau. Sử dụng jenkins để làm CICD đã giúp nhóm anh tiết kiệm được 30% khối lượng công việc và thời gian phát triển sản phẩm mà lại cho năng suất cao.

Chính vì lợi ích này thì hầu như công ty nào cũng sử dụng tool để làm CICD. Vậy khi nhắc đến CICD thì các em nghĩ ngay đến việc <b>tự động tích hợp và tự động deploy</b>, nó giúp tiết kiệm thời gian và chi phí.

<br>
# **4. Các em hãy xem demo dưới đây để thấy rõ hơn ưu điểm của CICD**
{% include youtubePlayer.html id=page.youtubeId %}
