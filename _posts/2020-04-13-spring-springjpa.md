---
layout: course-spring-web
title: Sử dụng Spring Data JPA
slug : spring-jpa
category: laptrinhspring
tags: [spring-web]
summery: Spring Data JPA
image: /images/blog/spring.png
description : Spring jpa là gì ? Khái niệm ORM, JPA và mô hình MVC. Hướng dẫn cấu hình sping jpa trong lập trình dự án Spring
youtubeId: 4dQlWJQ7ZQo
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em ,chủ đề hôm nay của anh là về <b>JPA</b> ? Anh sẽ giải thích nó là gì ? Cấu hình dự án sử dụng JPA ra sao ?
Đồng thời anh sẽ giới thiệu các cách truy vấn dữ liệu trong <b>database</b>.

<br>
# **1. ORM là gì ?**

<b>ORM</b> là viết tắt của Object Relational Mapping, là một quá trình ánh xạ (chuyển đổi) dữ liệu từ ngôn ngữ <b>hướng đối tượng</b> sang <b>Database</b> quan hệ và ngược lại.
ORM giúp mình ánh xạ các <b>tables,column,kiểu dữ liệu và mối quan hệ</b> (1-1,1-n,n-n) trong database thành các Class và thuộc tính trong Java.
Anh lấy ví dụ. Trong database mình có table (person)  và các trường (id kiểu Integer , name kiểu varchar ) như sau.

{% highlight mysql linenos %}
CREATE TABLE persons (
    id integer NOT NULL,
    name varchar(50) NOT NULL, salary float, PRIMARY KEY(id)
);
{% endhighlight %}

Như vậy ORM nghĩa là tương ứng với table person trong database mình ánh xạ nó trong Class Java (POJO) như sau cho tương ứng.

{% highlight java linenos %}
public class Person {
    public String name;
    public float salary;
    public Person(String name) { ... }
}
{% endhighlight %}

Như vậy trong database có gì, thì Class Java sẽ mô tả lại y chang vậy.
Sau đây là bản mapping các kiểu dữ liệu trong mysql tương ứng với kiểu Java <br>.

{:refdef: style="text-align: center;"}
![Cấu trúc dự án](/images/post/spring/mysql-java.jpg){:class="img-responsive"}
{: refdef}

<br>
# **2. Một số ORM Framework**

Trong <b>Spring</b> thì thường mình  hay sử trong các dự án Java được cung cấp bởi nhà cung cấp sau.

- JPA
- Hibernate
- OpenJPA
- EclipseLink
- Apache Cayenne

<br>
# **3. JPA là gì ?**

<b>JPA</b> viết tắc của từ Java Persitent API . Tầng Persistent có nhiệm vụ thao  tác với database như query lấy dữ liệu , lưu dữ liệu
xuống database . JPA cung cấp cho mình cơ chế ORM mapping các bảng, column , mối quan hệ trong database thành các lớp java và đồng
thời cung cấp cho mình các method cần thiết để thao tác  dữ liệu trong database.

<br>
# **4. Vai trò của tầng Persistent**

{:refdef: style="text-align: center;"}
![Tầng Persis](/images/post/spring/persistentlayer.jpg){:class="img-responsive"}
{: refdef}

1. Như ta thấy ở hình trên, đó chính là luồng đi của một ứng dụng . Bắt đầu khi người dùng gửi request lên server.
2. Khi request vào Dispatcher nó sẽ đưa đến Controller tương ứng để xử lý request
3. Từ Controller nó sẽ gọi xuống Service để thực hiện các nghiệp vụ cần thiết
4. Từ tầng Service nó gọi tầng Persisten (Trong các dự án mình sử dụng JPA) để thực hiện các thao tác xuống database và trả kết quả về

<br>
# **5. Hướng dẫn sử dụng JPA thông qua ví dụ**

Sau đây mình sẽ làm một ứng dụng đơn giản để lấy dữ liệu từ <b>database</b> và trả kết quả về cho người dùng. Và mình sẽ sử dụng thư viện spring-data-jpa để kết nối và thao tác với database.
Ngoài ra mọi người có thể xem qua bài viết Hibernate mà anh đã viết để thao tác với database nhé. Source code <a href="https://github.com/codegymdanang/CGDN-SpringBoot-JPA"> tại đây </a>.


#### Bước 1 -  Chuẩn bị dependency trong file pom.xml

{% highlight java linenos %}
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-jpa</artifactId>
        </dependency>

         <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <scope>runtime</scope>
         </dependency>

{% endhighlight %}
<br>

#### Bước 2 - Cấu hình connection kết nối database trong file application.properties

{% highlight java  %}
spring.datasource.driver-class-name=com.mysql.jdbc.Driver
spring.datasource.url=jdbc:mysql://localhost:3306/company
spring.datasource.username=root
spring.datasource.password=abc  
{% endhighlight %}
<br>

#### Bước 3 - Chuẩn bị entiry . Mapping  table Department trong database thành các class Java

{% highlight java linenos %}
@Data
@Entity
@Table(name = "department")
@NamedQuery( name="findAllCustomersWithName",
        query="SELECT c FROM Customer c WHERE c.name LIKE :custName" )
public class Department implements Serializable {

    @Column(name = "id")
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Id
    public int id;

    @Column(name = "name")
    public String name;

    @Column(name = "description")
    public String description;


}
{% endhighlight %}
<br>

#### Bước 4 - Chuẩn bị Controller để mapping request từ client

{% highlight java linenos %}
@Controller
public class CreationQueryController {


    @Autowired
    DepartmentQueryCreationService departmentQueryCreationService;

    @GetMapping("/creationFindbyDepartmentName/{name}")
    public ModelAndView findbyDepartment(@PathVariable("name") String name) {
        ModelAndView modelAndView = new ModelAndView("creation");
        List<Department> departments = departmentQueryCreationService.findByDepartment(name);
        modelAndView.addObject("departments",departments);
        return modelAndView;

    }
}
{% endhighlight %}
<br>

#### Bước 5 - Tạo file DepartmentQueryCreationService Service

Service có nhiệm vụ thực hiện các nghiệp vụ của ứng dụng . Đồng thời nhúng bean Repository để gọi tầng Persistence.

{% highlight java linenos %}
@Service
public class DepartmentQueryCreationService {

    @Autowired
    DepartmentQueryCreationRepository departmentQueryCreationRepository;

    public List<Department> findByDepartment(String name) {
        return departmentQueryCreationRepository.findByName(name);
    }
}
{% endhighlight %}
<br>

#### Bước 6 - Tạo file DepartmentAnnotationRepository sử dụng JPA

Tầng này có nhiệm vụ thao tác lấy dữ liệu. Các cách lấy dữ liệu sẽ được giới thiệu riêng ở bài khác.

{% highlight java linenos %}
@Transactional
public interface DepartmentAnnotationRepository extends JpaRepository<Department,Integer> {

    @Query("select department from Department department where department.name = ?1")
    Department findByName(String departmentName);

    @Query("select department from Department department where department.name like %?1")
    List<Department> findByFirstnameEndsWith(String departmentName);

    @Query(value = "select department from Department department where department.name = ?1", nativeQuery = true)
    Department findByName2(String departmentName);
}
{% endhighlight %}
<br>

#### Bước 7 - Luồng đi của ứng dụng trên như sau

1. Người dùng gõ vào link là http://localhost8080/creationFindbyDepartmentName/java
2. Request trên sẽ được Controller CreationQueryController xử lý nhờ cơ chế mapping
3. Trong CreationQueryController ta nhúng DepartmentQueryCreationService để gọi hàm từ service này
4. DepartmentQueryCreationService có nhiệm vụ thực hiện các nghiệp vụ của chương trình đồng thời nhúng DepartmentQueryCreationRepository
để gọi hàm từ DepartmentQueryCreationRepository.
5. DepartmentQueryCreationRepository có nhiệm vụ truy vấn dữ liệu trong database và trả kết quả lại cho Service. Service trả kết quả cho
Controller . Cuối cùng từ Controller trả kết quả cho client.

##### Như vậy ta có thể phân ra thành 2 luồng chính

Luồng 1 : Lấy dữ liệu mình bắt đầu từ Client . <br>
Client -> Controller -> Service -> JPA -> Query database .<br>
Luống 2 : Trả dữ liệu từ Database .<br>
Database -> JPA -> Service -> Controller -> Client .

<br>
# **6. Kết luận**

Tổng hợp các các cách  query xuống database .
1. Sử dụng Query Creation
2. Sử dụng @Query (ở ví dụ trên khi ta dùng @Query)
3. Sử dụng @NameQuery
4. Sử dụng EntityManager  

<br>
# Tại sao mình cần JPA

1. Chúng ta chỉ tập trung vào viết chức năng của chương trình còn các việc như quản lý connection , cách query thì JPA sẽ lo
2. Khả năng thay đổi database không bị ảnh hưởng . Ví du hôm nay ta dùng Mysql ngày mai ta dùng Postgres thì không ảnh hưởng tới
chương trình của mình.

<br>
# **8. Video demo cách sử dụng JPA**

{:refdef: style="text-align: center;"}
{% include youtubePlayer.html id=page.youtubeId %}
{: refdef}
