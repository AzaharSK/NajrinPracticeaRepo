# 🌱 Java Spring Framework – Interview‑Ready Notes

---

## 1. What is Spring Framework?

- Spring is a **lightweight, open‑source Java framework** for building **enterprise‑level applications**
- It provides features such as **Dependency Injection(DI)**, **Inversion of Control(IOC)**, **Aspect-Oriented Programming(AOP)**, 
- It also provides declarative **transaction management** , **logging**, **security**, and seamless integration with ORM frameworks like **Hibernate** for efficient database operations.
- Spring offers a rich ecosystem of modules (Spring MVC, Spring JDBC, Spring ORM, and Spring Security ) for end-to-end rapid App development and serves as the foundation for Spring Boot.


### Key Problems Spring Solves
- Tight coupling between classes
- Complex object creation, boilerplate codes
- Reduces repetitive code in JDBC, transactions, and configuration.
- Difficult testing with mocks and dependency injection.
- Spring solves complexity, tight coupling, and boilerplate in enterprise Java applications.

---

## 2. Advantages of Spring

- ♻️ __Lightweight Opensource and modular:__ – you use only what you need, reducing application complexity.
- 🔁 __Loose coupling with Dependency Injection (DI) & Inversion of Control mechanism:__ – improves code maintainability, testing, and flexibility.
- 🧪 __Powerful transaction management:__ – supports declarative transactions across databases and ORM , Messaging , Security and tools like Hibernate.
- ♻️ __AOP support:__ – cleanly handles cross-cutting concerns such as logging, security, and auditing.
- 🔌 __Easy integration:__ – works seamlessly with Hibernate, JPA, JDBC, REST, messaging, and other frameworks.
- 🔁 __Spring Boot support:__ – enables **Rapid** end-to-end App development development with minimal configuration.
- 🧪 __Easy unit & integration testing:__  Mocking object supported with dependency injection
- ♻️ __Strong community and ecosystem:__  excellent documentation, tools, and long-term support.

---

## 3. Inversion of Control (IoC)

- IoC means **control of object creation is given to Spring**
- Developer does **not use `new` keyword** directly
- Spring container manages object lifecycle

### IoC Containers

- **BeanFactory** – basic container
- **ApplicationContext** – advanced (recommended)

---

## 4. Dependency Injection (DI)

- DI is a design pattern
- Dependencies are injected by Spring container

### Types of Dependency Injection

1. **Constructor Injection** (Recommended)
2. Setter Injection
3. Field Injection

### Example – Constructor Injection

```java
@Component
class Engine {
    void start() {
        System.out.println("Engine started");
    }
}

@Component
class Car {
    private final Engine engine;

    @Autowired
    public Car(Engine engine) {
        this.engine = engine;
    }
}
```

---

## 5. Spring Beans

- A **Bean** is an object managed by Spring container
- Defined using annotations or XML

### Bean Scopes

- `singleton` (default)
- `prototype`
- `request`
- `session`

```java
@Component
@Scope("prototype")
class UserService {}
```

---

## 6. Bean Life Cycle

### Bean Life Cycle Phases

1. Bean Instantiation
2. Dependency Injection
3. Initialization
4. Ready for use
5. Destruction

### Life Cycle Annotations

```java
@PostConstruct
public void init() {
    System.out.println("Bean initialized");
}

@PreDestroy
public void destroy() {
    System.out.println("Bean destroyed");
}
```

---

## 7. Spring Annotations (Very Important ⭐)

### Stereotype Annotations

- `@Component` – generic
- `@Service` – business logic
- `@Repository` – DAO layer
- `@Controller` – MVC controller
- `@RestController` – REST APIs

### Dependency Injection

- `@Autowired`
- `@Qualifier`
- `@Primary`

---

## 8. What is Spring Boot?

- Built on top of Spring Framework
- Eliminates XML configuration
- Provides **auto‑configuration**
- Comes with **embedded servers** (Tomcat)

### Benefits of Spring Boot

- Faster development
- Production‑ready features
- Minimal configuration

---

## 9. Spring Boot Application Structure

```java
@SpringBootApplication
public class DemoApplication {
    public static void main(String[] args) {
        SpringApplication.run(DemoApplication.class, args);
    }
}
```

### `@SpringBootApplication` Includes

- `@Configuration`
- `@EnableAutoConfiguration`
- `@ComponentScan`

---

## 10. REST Controller

- Used to build RESTful web services
- Returns JSON/XML response

```java
@RestController
@RequestMapping("/api")
public class HelloController {

    @GetMapping("/hello")
    public String hello() {
        return "Hello Spring";
    }
}
```

---

## 11. MVC vs REST

| MVC | REST |
|---|---|
| Returns View (HTML) | Returns Data (JSON) |
| `@Controller` | `@RestController` |
| Used for UI apps | Used for APIs |

---

## 12. application.properties

- Used for configuration
- Environment‑specific values

```properties
server.port=8081
spring.datasource.url=jdbc:mysql://localhost:3306/test
spring.datasource.username=root
spring.datasource.password=root
```

---

## 13. JPA & Hibernate

- Hibernate is an ORM framework
- JPA is a specification

### Entity Example

```java
@Entity
@Table(name = "users")
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
}
```

### Repository

```java
public interface UserRepository extends JpaRepository<User, Long> {}
```

---

## 14. Common Interview Questions

- Difference between `@Component` and `@Service`?
- Why constructor injection is preferred?
- What is auto‑configuration?
- Difference between JPA and Hibernate?
- What is embedded server in Spring Boot?

---

## 15. Quick Interview Tips

- Prefer **constructor injection**
- Avoid field injection in production
- Know annotations clearly
- Explain concepts with examples

---

✅ **End of Notes** – Ready to push as `JavaSpringNotes.md` to GitHub 🚀




# Spring Data JPA and Hibernate

## What is Spring Data JPA

How to use Spring Data JPA

Create Coupon Service Data Access Layer

Create Product Service Data Access Layer

What are the different Entity Object States

Wha are various JPA Associations

What is Cascading

What is Lazy Loading

What are two levels of caching

How to configure Second Level Cache
