---
layout: course-spring-web
title: Sử dụng Hibernate
slug : hibernate
category: laptrinhspring
tags: [spring-web]
summery: Hibernate
image: /images/blog/spring.png
description : Sử dụng Hibernate trong lập trình Spring. Biết cách cấu hình hibernate trong dự án Spring. Hướng dẫn thực hiện các câu truy vấn lấy dữ liệu.
youtubeId: WNfuVJptPnQ
---

{% include toc.html %}

# **Giới thiệu nội dung bài viết**

Chào các em ,chủ để hôm nay chúng ta sẽ tìm hiểu về <b>Hibernate</b> .

<br>
# **1. Giới thiệu Hibernate**

Như các em biết để hiển thị được dữ liệu lưu trữ trong cơ sở dữ liệu (database) ra cho người dùng thì mình phải thao tác xuống <b>database</b> như kết nối vào database .Sau đó thực hiện các <b>câu lệnh truy vấn</b> như select , insert, update , join các bảng .Cuối cùng là lấy dữ liệu từ database về và xử lý. Trong lập trình java mình may mắn có một <b>framework</b> giúp mình làm được tất cả các việc đó. Nó chính là  <b>Hibernate</b>.

Vì sao ta nên sử dụng framework , bởi vì nó đã có sẳn các thư viện như kết nối xuống database, thực hiện các <b>câu truy vấn</b> chúng ta chỉ sử dụng các thư việc có sẳn mà framework cung cấp và nhiệm vụ của chúng ta chỉ tập trung vào xử lý các nghiệp vụ của phần mềm.

<b>Hibernate</b> là một framework được sử dụng ở tầng <b>Persistence</b>. Tầng Persisten có nghĩa là lưu trử và sử lý dữ liệu trong một khoảng thời gian dài. Hibernate là mã nguồn mở , ta có thể nhúng vào dự án và dùng không phải trả tiền

Các chức năng được hỗ trợ khi ta sử dụng Hibernate

- Auto DDL : DDL có nghĩa là các câu lệnh <b>định nghĩa cấu trúc</b> để lưu trữ dữ liệu như create table , columns , kiểu dữ liệu trong database. Hiberate có thể tự động tạo table, columns, kiểu dữ liệu thông qua các annotaion mà ta thêm trong Entity mà ta không cần phải vào database tạo các table , column bằng tay

- Auto Primary Key : Trong database để đánh dấu một trường là <b>khoá chính</b> thì ta phải làm bằng tay hoặc viết câu lệnh SQL để đánh dấu một trường là khoá chính của table. Hibernate có thể làm việc này một cách tự động

- HQL query : Để thực hiện các <b>câu lệnh truy vấn và thao tác dữ liệu</b> thì ta dùng cú pháp HQL (Hibernate Query Language) để lấy dữ liệu ra thay vì viết câu lệnh SQL như select * from table . Mà chúng ta có thể viết bằng ngôn ngữ HQL như select customer from customer customer . Khi sử dụng HQL thì ta không phụ thuộc vào database đang sử dụng là gì vì câu lệnh HQL nó tương thích với các database quan hệ khác nhau như mysql , postgress .Giúp chúng ta không phụ thuộc vào database.

- Hibernate Cache : giúp chúng ta có thể <b>cache (lưu lại câu query)</b> lại câu truy vấn mà không phải thực hiện thao tác, truy xuất xuống database nhiều lần. A ví dụ như câu select * from customer trả về 1000 kết quả. những kết quả này sẽ được lưu lại trong bộ nhớ. Khi có câu lại có câu lệnh select * from customer lần nữa. Vì nó đã lưu kết quả trong bộ nhớ nên nó sẽ trả về 1000 kết quả giống lần đầu tiên vì câu query giống nhau. Như vậy các em thấy dù có 1000 câu truy vấn thì Hibernate chỉ kết nối xuống database lần đầu tiên thôi. Điều này giúp cho ứng dụng nhanh hơn vì không phải mất thời gian kết nối xuống database và thực hiện truy vấn thêm nữa.

- Hibernate hỗ trợ <b>ORM mapping</b>. Các em có thể xem lại bài blog về ORM anh đã viết để nắm rõ thêm ORM là gì ?

- Hầu hết các dự án Java ngày nay đều sử dụng <b>Spring Data JPA</b> kết hợp với <b>Hibernate</b> như một công cụ để thao tác giữa ứng dụng của mình và database

<br>
# **2. Cấu hình Hibernate với Spring**

#### Bước 1 : Nhúng thư viện hibernate vào dự án qua file pom

{% highlight java linenos %}
<dependency>
   <groupId>org.hibernate</groupId>
   <artifactId>hibernate-core</artifactId>
   <version>4.3.6.Final</version>
</dependency>

<dependency>
   <groupId>org.javassist</groupId>
   <artifactId>javassist</artifactId>
   <version>3.18.2-GA</version>
</dependency>

<dependency>
   <groupId>mysql</groupId>
   <artifactId>mysql-connector-java</artifactId>
   <version>5.1.32</version>
   <scope>runtime</scope>
</dependency>

<dependency>
    <groupId>org.apache.tomcat</groupId>
    <artifactId>tomcat-dbcp</artifactId>
    <version>7.0.55</version>
</dependency>

{% endhighlight %}

#### Bước 2 : Tạo file khai báo kết nối database

Chúng ta tạo file <b>persistence-mysql.properties</b> khai báo username , database trong file properties. Khi spring chạy nó sẽ vào đây dể biết được phải kết nối database ở đâu .   

{% highlight java linenos %}
# jdbc.X
jdbc.driverClassName=com.mysql.jdbc.Driver
jdbc.url=jdbc:mysql://localhost:3306/spring_hibernate_dev?createDatabaseIfNotExist=true
jdbc.user=tutorialuser
jdbc.pass=tutorialmy5ql

# hibernate.X
hibernate.dialect=org.hibernate.dialect.MySQL5Dialect
hibernate.show_sql=false
hibernate.hbm2ddl.auto=create-drop

{% endhighlight %}

#### Bước 3 :Chúng ta có thể cấu hình Hibernate qua Java  

{% highlight java linenos %}
@Configuration
@EnableTransactionManagement
@PropertySource({ "classpath:persistence-mysql.properties" })
@ComponentScan({ "levunguyen.spring.persistence" })
public class PersistenceConfig {

   @Autowired
   private Environment env;

   @Bean
   public LocalSessionFactoryBean sessionFactory() {
      LocalSessionFactoryBean sessionFactory = new LocalSessionFactoryBean();
      sessionFactory.setDataSource(restDataSource());
      sessionFactory.setPackagesToScan(
        new String[] { "levunguyen.spring.persistence.model" });
      sessionFactory.setHibernateProperties(hibernateProperties());

      return sessionFactory;
   }

   @Bean
   public DataSource restDataSource() {
      BasicDataSource dataSource = new BasicDataSource();
      dataSource.setDriverClassName(env.getProperty("jdbc.driverClassName"));
      dataSource.setUrl(env.getProperty("jdbc.url"));
      dataSource.setUsername(env.getProperty("jdbc.user"));
      dataSource.setPassword(env.getProperty("jdbc.pass"));

      return dataSource;
   }

   @Bean
   @Autowired
   public HibernateTransactionManager transactionManager(
     SessionFactory sessionFactory) {

      HibernateTransactionManager txManager
       = new HibernateTransactionManager();
      txManager.setSessionFactory(sessionFactory);

      return txManager;
   }

   @Bean
   public PersistenceExceptionTranslationPostProcessor exceptionTranslation() {
      return new PersistenceExceptionTranslationPostProcessor();
   }

   Properties hibernateProperties() {
      return new Properties() {
         {
            setProperty("hibernate.hbm2ddl.auto",
              env.getProperty("hibernate.hbm2ddl.auto"));
            setProperty("hibernate.dialect",
              env.getProperty("hibernate.dialect"));
            setProperty("hibernate.globally_quoted_identifiers",
             "true");
         }
      };
   }
}
{% endhighlight %}

#### Bước 4. Tạo entity (ORM)

{% highlight java linenos %}
@Entity
@Table(name = "EMPLOYEE")
public class Employee {

	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	@Column(name = "emp_id")
	private long id;

	@Column(name = "emp_name")
	private String name;

	@Column(name = "emp_salary")
	private double salary;

	@OneToOne(mappedBy = "employee")
	@Cascade(value = org.hibernate.annotations.CascadeType.ALL)
	private Address address;
{% endhighlight %}

#### Bước 5. Sử dụng truy vẫn dữ liệu

Chúng ta sử dụng <b>sessionFactory</b> để mở kết nối và thực hiện các câu lệnh truy vấn xuống database.

{% highlight java linenos %}
public abstract class HibernateDAO{
 
   @Autowired
   SessionFactory sessionFactory;

   protected Session getCurrentSession(){
      return sessionFactory.getCurrentSession();
   }

   public  void query(String[] args) {

		//Prep work
		Session session = sessionFactory.getCurrentSession();

		//HQL example - Get All Employees
		Transaction tx = session.beginTransaction();
		Query query = session.createQuery("from Employee");
		List<Employee> empList = query.list();
		for(Employee emp : empList){
			System.out.println("List of Employees::"+emp.getId()+","+emp.getAddress().getCity());
		}

		//HQL example - Get Employee with id
		query = session.createQuery("from Employee where id= :id");
		query.setLong("id", 3);
		Employee emp = (Employee) query.uniqueResult();
		System.out.println("Employee Name="+emp.getName()+", City="+emp.getAddress().getCity());

		//HQL pagination example
		query = session.createQuery("from Employee");
		query.setFirstResult(0); //starts with 0
		query.setFetchSize(2);
		empList = query.list();
		for(Employee emp4 : empList){
			System.out.println("Paginated Employees::"+emp4.getId()+","+emp4.getAddress().getCity());
		}

		//HQL Update Employee
		query = session.createQuery("update Employee set name= :name where id= :id");
		query.setParameter("name", "Pankaj Kumar");
		query.setLong("id", 1);
		int result = query.executeUpdate();
		System.out.println("Employee Update Status="+result);

		//HQL Delete Employee, we need to take care of foreign key constraints too
		query = session.createQuery("delete from Address where id= :id");
		query.setLong("id", 4);
		result = query.executeUpdate();
		System.out.println("Address Delete Status="+result);

		query = session.createQuery("delete from Employee where id= :id");
		query.setLong("id", 4);
		result = query.executeUpdate();
		System.out.println("Employee Delete Status="+result);

		//HQL Aggregate function examples
		query = session.createQuery("select sum(salary) from Employee");
		double sumSalary = (Double) query.uniqueResult();
		System.out.println("Sum of all Salaries= "+sumSalary);

		//HQL join examples
		query = session.createQuery("select e.name, a.city from Employee e "
				+ "INNER JOIN e.address a");
		List<Object[]> list = query.list();
		for(Object[] arr : list){
			System.out.println(Arrays.toString(arr));
		}

		//HQL group by and like example
		query = session.createQuery("select e.name, sum(e.salary), count(e)"
				+ " from Employee e where e.name like '%i%' group by e.name");
		List<Object[]> groupList = query.list();
		for(Object[] arr : groupList){
			System.out.println(Arrays.toString(arr));
		}

		//HQL order by example
		query = session.createQuery("from Employee e order by e.id desc");
		empList = query.list();
		for(Employee emp3 : empList){
			System.out.println("ID Desc Order Employee::"+emp3.getId()+","+emp3.getAddress().getCity());
		}

		//rolling back to save the test data
		tx.rollback();

		//closing hibernate resources
		sessionFactory.close();
	}

}

{% endhighlight %}

<br>
# **3. Kết luận**

Để kết nối và thao tác với <b>database</b> chúng ta có thể dùng <b>Hibernate framework</b> để mình truy xuất và thao tác các dữ liệu. Ngoài Hibernate thông thường các dự án Spring thì mình dùng Spring Data JPA (bài JPA là gì mọi người có thể tham khảo bài viết trước của anh).

Vậy Hibernate và Spring Data JPA thì khác biệt gì nhau. Trước tiên chúng ta phải hiểu các khái niệm sau

JPA : <b>Java Persistence API</b>, cung cấp các chuẩn để kết nối database , truy vấn dữ liệu, lưu trữ dữ liệu.

<b>Hibernate</b> là một trong số <b>provider</b> (nhà cung cấp dịch vụ trong việc thao tác với database) cài đặt và tuân thủ các chuẩn JPA để thao tác , lưu trữ và truy xuất dữ liệu

<b>Spring JPA</b> : là một tầng được xây dựng ở trên JPA. Nó abstract (trừa tượng hoá các thư viện). Chúng ta chỉ cần dùng và tập trung và nghiệp vụ giúp chúng ta dể dàng quản lý, maintain code.

Thông thường ở dự án Spring mình kết hợp cả 2. Mình sử dụng Hibernate là provider cho ORM , các validation và kết hợp với Spring Data JPA để thao tác với database.
