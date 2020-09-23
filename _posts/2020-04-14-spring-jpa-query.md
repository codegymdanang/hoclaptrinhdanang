---
layout: course-spring-web
title: Sử dụng JPA
slug : spring-jpa-query
category: laptrinhspring
tags: [spring-web]
summery: Spring JPA Query
image: /images/blog/spring.png
featureImage: /images/post/javacore/feature_jpa.png
description : Sử dụng JPA thao tác với database trong lập trình Spring. Hiểu được các annotation như @Query, Creation Query, Name Query và các annotaion bổ trợ trong việc truy vấn dữ liệu trong các ứng dụng spring hoặc spring boot.
youtubeId: bilwK0K9qoc
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em ,chủ để hôm nay chúng ta sẽ tìm hiểu về các cách để <b>query</b> dữ liệu từ database thông qua <b>Spring Data JPA</b>. 

Giả sử ta có ta viết một chương trình quản lý nhân sự ở một công ty. Thường ở một công ty sẽ có các phòng ban như : Phòng kế toán, phòng đào tạo, phòng nhân sự. Tại mỗi phòng ban sẽ có các nhân viên thuộc phòng ban đó. Ví dụ ta có entity Phòng ban như sau.


{% highlight java  linenos %}
@Entity
@Table(name = "phongban")
public class PhongBan implements Serializable {

    @Column(name = "id")
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Id
    public int id;

    @Column(name = "ten")
    public String name;

    @Column(name = "mota")
    public String description;
}
{% endhighlight %}

<br>
# **1. Sử dung @Query để lấy dữ liệu trong table Department ?**

- Sử dụng <b>JPQL</b>

{% highlight java  linenos %}
@Transactional
public interface PhongBanAnnotationRepository extends JpaRepository<PhongBan,Integer> {

    @Query("select phongban from PhongBan phongban)
    PhongBan findAllPhongBan();
}
{% endhighlight %}

- Sử dụng <b>Native Query</b>

{% highlight java  linenos %}
@Query(
  value = "SELECT * FROM PhongBan phongban WHERE phongban.status = 1",
  nativeQuery = true)
Collection<PhongBan> findAllPhongBan();
{% endhighlight %}

Để sử dung câu query thuần giống như ta thực hiện câu select trong database thì mình thêm tham số nativeQuery = true

- Tham số <b>Index</b> trong câu Query

{% highlight java  linenos %}
@Query("select phongban from PhongBan phongban where phongban.name = ?1")
    PhongBan findByName(String tenphongban);
{% endhighlight %}

Chúng ta dùng ?1 tương ứng với tham số đầu tiên trong method findByName. ?1 sẽ được ánh xạ bằng tham số String tenphongban. Nếu
chúng ta có nhiều tham số ví dụ

{% highlight java  linenos %}
@Query("select phongban from PhongBan phongban where phongban.name = ?1" and phongban.code = ?2)
    PhongBan findByName(String tenphongban,int code);
{% endhighlight %}

Lúc đó ?1 sẽ bằng tham số tenphongban và ?2 bằng code. Như vậy dùng ? để chỉ ra thứ tự các tham số trong method tương ứng với vị trí trong câu query

- Tham số <b>Name</b> trong câu Query

{% highlight java  linenos %}
@Query("SELECT nguoidung FROM NguoiDung nguoidung WHERE nguoidung.status = :status and nguoidung.name = :name")
User findUserByStatusAndNameNamedParams(@Param("status") Integer status, @Param("name") String name);
{% endhighlight %}

Nó cũng giống na ná như Index query thay vì sử dụng vị trí (index), thì ta sử dung cái tên . Ví dụ trên ta sử dụng :status , :name để ánh xạ vào đúng tên (@Param("status") Integer status, @Param("name") String name) trong phương thức. Chú ý là ta sử dụng thêm @Param để ánh xạ tên method và tên trong @Query giống nhau

- Collection Parameter

Trong database chúng ta có toán tử IN và NOT IN như sau

{% highlight java  linenos %}
SELECT nguoidung FROM NguoiDung nguoidung WHERE nguoidung.name IN :names
{% endhighlight %}

Để sử dụng được toán tử IN trong <b>JPQL Query</b> thì ta sử dụng tham số là Collection như sau

{% highlight java  linenos %}
@Query(value = "SELECT nguoidung FROM NguoiDung nguoidung WHERE nguoidung.name IN :names")
List<User> findUserByNameList(@Param("names") Collection<String> names);
{% endhighlight %}

<br>
# **2. Sử dung Query Creation**

<b>Spring Data JPA</b> hỗ trở cho chúng ta sẳn các phương thức để truy cập xuống database. Chúng ta chỉ cần kế thừa JPARepository và sau đó có thể sử dụng các phương thức mà JPA cung cấp đề lấy dữ liệu từ database.

{% highlight java  linenos %}
public interface PhongBanQueryCreationRepository extends JpaRepository<PhongBan,Integer> {

    List<PhongBan> findByName (String name);
    List<PhongBan> findByNameLike (String name);
    List<PhongBan> findByNameContaining (String name);
    List<PhongBan> findByNameStartingWith(String name);
    List<PhongBan> findByNameEndingWith(String name);
    List<PhongBan> findByNameIgnoreCase(String name);


    List<Department> findByNameAndLocal(String name,String local);
    List<PhongBan> findByNameOrLocal(String name,String local);
    List<PhongBan> findByNameNot(String name);
    List<PhongBan> findByDateAfter(Date date);
    List<PhongBan> findByDateBefore (Date date);
    List<PhongBan> findByDateBetween(Date from,Date to);

}
{% endhighlight %}

Trong đó <b>findBy</b> là từ khoá mà JPA cung cấp cho mình sau từ findBy là tên column có trong database. Ví dụ findByName tìm kiếm các user có tên là tham số name truyền vào. Trong đó findBy là từ khoá của JPA và Name chính là tên column trong database. Ngoài findBy thì JPA còn hỗ trợ nhiều phương thức khác nữa có thể xem ở đây

<br>
# **3. Sử dung @NameQuery trong Entiry**

{% highlight java  linenos %}
@Entity
@Table(name = "NhanVien")
@NamedQuery(name = "NhanVien.fetchByLastNameLength",
        query = "SELECT e FROM NhanVien e WHERE CHAR_LENGTH(e.lastname) =:length "
)
public class NhanVien {

    @Id
    @Column(name = "id")
    @GeneratedValue(strategy = GenerationType.SEQUENCE)
    private Long id;

    @Column(name = "firstname")
    private String firstName;

    @Column(name = "lastname")
    private String lastname;
 }
{% endhighlight %}     

Như các em thấy trong Class Entity mình sử dụng <b>@NameQuery</b> để tạo câu lệnh select. Chú ý cho anh chổ @NamedQuery(name = "NhanVien.fetchByLastNameLength") Để gọi được câu lệnh này thì nơi chỗ JPA Repository ta phải có phương thức (fetchByLastNameLength) giống y chang vậy.

{% highlight java  linenos %}
@Repository
public interface NhanVienRepository extends JpaRepository<Employee,Long>, EmployeeRepositoryCustom {

    List<NhanVien> fetchByLastNameLength(@Param("length") Long length);
}
{% endhighlight %}

<br>
# **4. Sử dung Order in Query để sắp xếp dữ liệu theo chiều tăng hoặc giảm dần**

{% highlight java  linenos %}
phongBanRepository.findAll(new Sort(Sort.Direction.ASC, "name"));
{% endhighlight %}

Dòng <b>new Sort(Sort.Direction.ASC, "name")</b> nghĩa là chúng ta muốn sắp xếp dữ liệu ở cột name theo chiều hướng tăng dần. Nếu muốn sắp xếp name theo chiều hướng giảm dần thì ta dùng new Sort(Sort.Direction.DESC, "name")

<br>
# **5. Sử dụng annotation @Modifying để cập nhật dữ liệu**

{% highlight java  linenos %}
@Modifying
@Query("update NhanVien nhanvien set nhanvien.status = :status where nhanvien.name = :name")
int updateUser(@Param("status") Integer status,
  @Param("name") String name);
{% endhighlight %}

Kết quả trả về là bao nhiêu dòng trong database được cập nhật. Chúng ta cũng có thể sử dụng Native Query để cập nhật như sau

{% highlight java  linenos %}
@Modifying
@Query(value = "update NhanVien nhanvien set nhanvien.status  where nhanvien.name = ?",
  nativeQuery = true)
int updateUserNative(Integer status, String name);
{% endhighlight %}

<br>
# **6. Sử dụng annotation @Modifying để insert dữ liệu**

Trong <b>spring data jpa</b> chúng ta dùng hàm save() có sẳn để insert dữ liệu xuống database. Trong trường hợp dùng native query thì chúng ta phải kết hợp <b>@Modifiying</b> và câu lệnh Insert chung với nhau vì Spring Data JPA chúng ta đang dùng không hổ trợ Insert

{% highlight java  linenos %}
@Modifying
@Query(
  value =
    "insert into NhanVien (name, age, email, status) values (:name, :age, :email, :status)",
  nativeQuery = true)
void insertNhanVien(@Param("name") String name, @Param("age") Integer age,
  @Param("status") Integer status, @Param("email") String email);
{% endhighlight %}

# **7. Sử dụng Pageable để phân trang**

Chúng ta sử dụng <b>Pageable</b> để lấy một tập hợp con trong database. Ví dụ như trong database có 100 dòng. Ta chỉ muốn lấy từ dùng 1 cho tới dòng 10. Để làm được như vậy chúng ta sẽ sử dụng đối tượng <b>PageRequestObject</b> để khai báo số lượng dòng mà ta muốn trả về , sau đó truyền đối tượng PageRequestObject vào câu lệnh truy vấn.

{% highlight java  linenos %}
Pageable first10PageWithTwoElements = PageRequest.of(0, 10);
Page<Product> allProducts = productRepository.findAll(first10PageWithTwoElements);
{% endhighlight %}

{% highlight java  linenos %}
public interface ProductRepository extends PagingAndSortingRepository<Product, Integer> {

    List<Product> findAllByPrice(double price, Pageable pageable);
}
{% endhighlight %}

{:refdef: style="text-align: center;"}
{% include youtubePlayer.html id=page.youtubeId %}
{: refdef}
