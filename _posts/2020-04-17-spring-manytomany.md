---
layout: course-spring-web
title: Sử dụng ManyToMany Relationship
slug : many-to-many
category: laptrinhspring
tags: [spring-web]
summery: Many To Many
image: /images/blog/spring.png
featureImage: /images/post/javacore/feature_manytomany.png
description : Sử dụng annotation @ManyToMany trong lập trình Spring. Hướng dẫn sử dụng quan hệ @ManyToMany many to many trong spring data jpa . Cấu hình và triển khai dự án dùng @ManyToMany
youtubeId: qhovNzYD5Lk
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em ,chủ đề hôm nay chúng ta sẽ nói về annotation <b>@ManyToMany</b>. 

<br>
# **1. ManyToMany là gì**

Hôm nay mình sẽ làm phần mềm về quản lý  sinh viên và khoá học tại trường đại học. Như các em đã biết
Một sinh viên có thể đăng ký học nhiều khoá học (khoá anh văn , khoá tin học, khoá hoá học) trong một học kỳ.
Một khoá học thường sẽ có rất nhiều sinh viên đăng ký theo học trung bình một lớp thường có 30 bạn.
Như vậy mình sẽ thấy mối quan hệ giữa sinh viên và khoá học là quan hệ nhiều nhiều. Một học sinh có nhiều khoá học và một khoá học có
nhiều sinh viên.

<br>
# **2. Biểu diển ManyToMany trong database**

Chúng ta sẽ biểu diển mối quan hệ này trong database. Như các em biết trong database nếu 2 tables quan hệ nhiều nhiều mình sẽ tách thêm
một bảng thứ 3 làm bảng trung gian cho 2 tables đó . Chúng ta sẽ tạo thêm một bảng trung gian là student_course như sau.

{% highlight mysql  linenos %}
CREATE TABLE `student` (
  `id` int(11) unsigned NOT NULL AUTO_INCREMENT,
  PRIMARY KEY (`cart_id`)
) ENGINE=InnoDB AUTO_INCREMENT=5 DEFAULT CHARSET=utf8;

CREATE TABLE `course` (
  `id` int(11) unsigned NOT NULL AUTO_INCREMENT,
  PRIMARY KEY (`id`),
) ENGINE=InnoDB AUTO_INCREMENT=7 DEFAULT CHARSET=utf8;


CREATE TABLE `student_course` (
  `student_id` int(11) unsigned NOT NULL AUTO_INCREMENT,
  PRIMARY KEY (`id`),
  `course_id` int(11) unsigned NOT NULL AUTO_INCREMENT,
  PRIMARY KEY (`id`),
) ENGINE=InnoDB AUTO_INCREMENT=7 DEFAULT CHARSET=utf8;

{% endhighlight %}

Như các em thấy ở trên mình có thêm một table student_course có chứa column student_id là khoá phụ liên kết tới bảng Student
và column cours_id là khoá phụ liên kết tới bảng course. 2 cặp khoá phụ này kết hợp với nhau tạo thành khoá chính của bảng student_course.
Trong thiết kế database không tồn tại quan hệ nhiều nhiều chính vì vậy mà mình có thêm một bảng trung gian ở giữa để bẻ mối quan hệ nhiều nhiều thành 2 mối quan hệ một nhiều .   

<br>
# **3. Biểu diển ManyToMany trong Java**

Trong Java chúng ta sử dụng annotation <b>@ManyToMany</b> để thể hiện mối quan hệ nhiều nhiều.
Đầu tiên chúng ta sẽ tạo Entity Student

{% highlight java  linenos %}

@Entity
@Table(name = "student")
public class Student {

    @Id
    @Column(name = "id")
    private Long id;

    @ManyToMany
    @JoinTable(name = "student_course", joinColumns = @JoinColumn(name = "student_id"), inverseJoinColumns = @JoinColumn(name = "course_id"))
    private Set<Course> likedCourses;
}
{% endhighlight %}

Như các em thấy trong entity Student đầu tiên ta thấy

<b>@ManyToMany</b> : dùng để nói rằng Entity Student sẽ có mối quan hệ nhiều nhiều với Course

<b>@JoinTable</b> : mình chỉ ra table trung gian dùng để kết nối 2 bảng như ta thảo luận ở mục 1 trong phần database. Khi 2 tables quan hệ nhiều nhiều thì mình thêm một bảng trung gian. Trong bài này bảng trung gian mình có tên là student_course. Trong @JoinTable có 3 tham số sau 
 
Tham số đầu tiên là name = "student_id" cái này là ta đặt tên cho mối quan hệ là gì
Tham số thứ 2 là joinColumns = @JoinColumn(name = "student_id") Column mà bảng Student sẽ liên kết với bảng trung gian
Tham số thứ 3 inverseJoinColumns = @JoinColumn(name = "course_id") Column mà bảng Course sẽ liên kết với bảng trung gian


Như vậy là ta đã thiết lập xong table trung gian nối 2 bảng Student và Course có quan hệ nhiều nhiều. 


Tiếp đến ta khai báo entity Course

{% highlight java  linenos %}
@Entity
@Table(name = "course")
public class Course {

    @Id
    @Column(name = "id")
    private Long id;

    @ManyToMany(mappedBy = "likedCourses")
    private Set<Student> likes;
}

{% endhighlight %}

Như vậy là ta đã setup xong. Như trong thực tế ta có thể dùng nhiều cách để code mối quan hệ nhiều nhiều. Tiếp sau đây a sẽ trình bày kỷ
thuật CompositeKey để làm quan hệ nhiều nhiều. Mình ko cần dùng <b>@JoinTable</b>

<br>
# **4 . Quan hệ nhiều nhiều sử dụng CompositeKey**

Như ta thấy ở mục 1 về cấu trúc database. Ta có một bảng trung gian là student_course với 2 keys phụ là student_id và course_id. Hai khoá này kết hợp với nhau trở thành khoá chính và mình gọi là <b>Composite Key</b>.

Trong Java mình sẽ thể hiện nó như sau.

{% highlight java  linenos %}
@Embeddable
class CourseRatingKey implements Serializable {

    @Column(name = "student_id")
    Long studentId;

    @Column(name = "course_id")
    Long courseId;

    // standard constructors, getters, and setters
    // hashcode and equals implementation
}
{% endhighlight %}

Mình khai báo <b>@Embeddabl<b> để mình nhúng vào Entity mà nó sử dụng. Sau đây mình sẽ tạo Entity
StudentCouse và nhúng CourseRatingKey vào

{% highlight java  linenos %}
@Entity
@Table(name = "student_course")
public class StudentCouse {

    @EmbeddedId
    private CourseRatingKey id;

    @ManyToOne
    @MapsId("student_id")
    @JoinColumn(name = "student_id")
    private Student student;

    @ManyToOne
    @MapsId("course_id")
    @JoinColumn(name = "course_id")
    private Course course;
}
{% endhighlight %}

Như ta thấy ở trên mình không dùng <b>@ManyToMany</b> nữa mà thay vào đó là <b>@ManyToOne</b>. Entity StudentCouse sẽ link tới Entity  Student và Entity Course. Nó như là một bảng đóng vai trò trung gian

Chúng ta sử dụng <b>@EmbeddedId</b> để dánh dấu cặp key trở thành khoá chính (PRIMARY KEY ) trong entity

<br>
# **5. Tổng kết**

Các em có thể dùng một trong 2 cách trên khi gặp mối quan hệ nhiều nhiều đều giải quyết được vấn đề. Thông thường anh hay dùng cách thứ 2 (CompositeKey) vì code dể quản lý và thay đổi . Ví dụ như a muốn thêm vô vài trường trong table trung gian thì  quản lý rất dể.

{:refdef: style="text-align: center;"}
{% include youtubePlayer.html id=page.youtubeId %}
{: refdef}
