28/08/2020
[Alishev Guide](https://www.youtube.com/watch?v=5ePo08sqcpk)
[letsCode Guide](https://www.youtube.com/watch?v=jH17YkBTpI4&t=9s)
>## H2 Database + Spring MVC: Entity Class Example
```java
    package com.baeldung.h2db.springboot.models;
    
    import javax.persistence.Entity;
    import javax.persistence.GeneratedValue;
    import javax.persistence.Id;
    import javax.persistence.Table;
    
    @Table(name = "users")
    @Entity
    public class User {
    
        @Id
        @GeneratedValue
        private int id;
    
        private String firstName;
    
        private String lastName;
    
        public User() { }
    
        public int getId() {
            return id;
        }
    
        public void setId(int id) {
            this.id = id;
        }
    
        public String getFirstName() {
            return firstName;
        }
    
        public void setFirstName(String firstName) {
            this.firstName = firstName;
        }
    
        public String getLastName() {
            return lastName;
        }
    
        public void setLastName(String lastName) {
            this.lastName = lastName;
        }
    
        @Override
        public String toString() {
            return "User{" +
                    "id=" + id +
                    ", firstName='" + firstName + '\'' +
                    ", lastName='" + lastName + '\'' +
                    '}';
        }
    }
 ```
 30/08/2020
>## `@Controller`
```java
    @Controller
    public class MyController {
    	@GetMapping("/do_things")
    	public String doThings() {
    		return "do_things"; // html, for example
    	}
```
>Есть (зависит от HTTP-запроса):
>- @GetMapping
>- @PostMapping
>- @PutMapping
>- @DeleteMapping
>- @PatchMapping

>Чтобы все URL-адреса начинались с одного раздела:
```java
    @Controller
    @RequestMapping("/people")
    public class MyController {
    	@GetMapping("/do_things")
		//...
    	}
```
>**Good practice**: класть представления в папку, которая относится к определенному контроллеру.

31/08/20
>## GET Request Parameters
>Можно получить 2мя способами:
>HttpServletRequest (объект содержит вообще все параметры запроса, не подойдет, если надо достать один-два параметра):
```java
     @GetMapping("/hello")
	  public String helloPage(HttpServletRequest request) {
		  String name = request.getParameter("name");
		  //...
		  return "hello";
	}
```
>@RequestMapping:
```java
     @GetMapping("/hello")
	  public String helloPage(@RequestParam("name") String name) {
		  //...
		  return "hello";
	}
```
>Если не передать параметры в @RequestParam будет ошибка. Чтобы избежать ошибку:
```java
    @RequestParam(value="name", required=false)
```
>В HTML можем (тогда при вызове контроллера получим параметры):

    <a href="/hello?name=Tom&surname=Jones"></a>

>## Model
>Модель -- как контейнер для данных приложения. 
>Доступ к модели:
```java
    @GetMapping("/hello")
    public String helloPage(Model model) {
    	model.addAttribute("key", "value");
    	return "first/hello";
    }
```
>HTML:

    <p th:text="${message}"></p>
>В контроллере:
```java
    ... helloPage(@RequestParam("name") String name, Model model) {
    	model.addAttribute("message", name);
    	return ...
    }
```
06/09/2020
>## Creating Spring MVC Application
>Create project -> Maven -> добавить зависимости в pom.xml
>Все шаблоны помещаются в java -> resources
>Главный класс -- вход в приложение `SpringApplication.run(...)`
>Если не указывать маппинг -> страница откроется сразу при загрузке localhost:8080
>## Adding Database
>Добавляем БД в зависимости.
>resources -> config -> application.properties:

      ...datasource.url=...
      ...datasource.username=...
      ...datasource.password=...
      ...jpa.generate-ddl=true // Spring создаст структуру БД
>java -> com.example.app -> domain: Создаем класс-сущность, помечаем аннотацией `@Entity`; снабжаем геттерами/сеттерами.
>java -> com.example.app -> repos: Создаем интерфейс `EntityRepository`:
```java
    public interface EntityRepository extends CrudRepository<Entity, Long> {
	    //... тут пишем методы для обработки данных БД, 
	    // например, findByName() и т.д.
	    // по умолчанию есть findAll()
	}
```
>В классе-контроллере добавляем `@Autowired` зависимость `EntityRepository`.
>Если добавили в класс-сущность свой конструктор, то обязательно нужно добавить пустой конструктор.
>Объекты сохраняем в `EntityRepository`. Метод `findAll()` возвращает `Iterable`.
>## Spring Security: Authorization & Registration
>Делаем страницу лендинг на авторизацию/регистрацию.
>java -> com.example.app -> config -> MvcConfig.java (`registry.addViewController("/login").setViewName("login");`)
>Добавляем зависимость для Spring Security.
>config -> WebSecurityConfig.java: `@Autowired DataSource dataSource`
>Создаем шаблон для страницы входа/страницы авторизации. На главную страницу добавить логаут.
>*Главная страница -> Страница входа -> Страница для авторизации*

>**Настройка авторизации для пользователей:**
>Добавляем:
```java
    @Entity
    @Table(name="usr")
    public class User{
	    
	    // используем это, т.к. для небольших табиц, как Роли, можно не составлять 
	    // целую таблицу в БД, а сделать перечисление и привязать его.
	    // EAGER -- жадный, то есть все данные подгружаются сразу.
	    // LAZY -- ленивый, то есть данные подгружаются по мере востребования.
	    // мало данных -- EAGER, много данных -- LAZY
	    @ElementCollection(targetClass = Role.class, fetch = EAGER)
		
		// привязываем таблицу к таблице User по полю user_id
	    @CollectionTable(name = "user_role", joinColumns = 		@JoinColumn(name="user_id"))
		@Enumerated(EnumType.STRING)
    	private Set<Role> roles;
    	//...
    }
```
>domain -> `enum Role { USER; }`
>WebSecurityConfig.java:
```java
    @Overrided
    protected void configure(Auth...Builder) {
    	auth.jdbcAuth()
    	.dataSource(dataSource)
    	.passwordEncoder(...)
    	// система ищет пользователя по имени
    	.userByUsernameQuery("select username, password, active from usr where username=?") 
    	// таблицы user и user_role присоединяются по полю user_id = id, выбор имени и роли
    	.authoritiesByUsername("select u.username, ur.roles from usr u inner join user_role ur on u.id=ur.user_id where u.username=?") 
    }
```

>Добавляем шаблон страницы регистрации; на странице логина добавляем ссылку на страницу регистрации.
>java -> com.example.app -> controller -> RegistrationController.java : @GetMapping, @PostMapping
>repos -> UserRepository: `interface UserRepository extends JpaRepository<>`
>UserRepository: `findByUsername();`
>RegistrationController.java -> @PostMapping:
```java
    @PostMapping
    public String addUser(User user, Model model) {
    	User userFromDB = UserRepository.findByName(user.getUsername());
    	if user not null {
    		// отображаем сообщение на шаблоне
    		model.put("message", "User exists!"); /
    		return /registration;
    	} else {
    	user.setActive(true);
    	//???
    	user.setRoles(Collections.singleton(Role.USER));
    	userRepository.save(user);
    }
```
> Если нашли пользователя в БД -> пишем, что такой уже есть и его нельзя зарегистрировать; иначе -> меняем статус активности, назначаем роль и сохраняем пользователя в БД через репозиторий.
>## Spring Boot Jpa (Hibernate): Adding Relations to DB (1-N)

	

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA4NTIyMDM0N119
-->