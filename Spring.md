# 🌱 Java Spring Framework – Interview‑Ready Notes

---

## 1. What is Spring Framework?

- Spring is a **lightweight, open‑source Java framework** for building **enterprise‑level applications**
- It provides features such as **Dependency Injection(DI)**, **Inversion of Control(IOC)**, to manage the object cration & lifecycle by framework itself, 
- It also provides  **Aspect-Oriented Programming(AOP)** , declarative **transaction management** , **logging**, **security**, and seamless integration with ORM frameworks like **Hibernate** for efficient database operations.
- Spring offers a rich ecosystem of modules (Spring MVC, Spring JDBC, Spring Data, Spring ORM, and Spring Security ) for end-to-end rapid App development and serves as the foundation for Spring Boot.


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

- Inversion of Control (IoC) is a design principle , where Spring container takes control of object creation and dependency management instead of the application code.
- That is  👉 Instead of the developer creating objects using **new** operator, Spring creates, manages, and injects them. 
- Developer does **not use `new` keyword** directly
- Spring container manages object lifecycle, object creation and dependency management is transferred from the program to the Spring container.

### Traditional Approach (Without IoC)

```java
Engine engine = new PetrolEngine();
Car car = new Car(engine);

// Developer controls object creation
// Tight coupling between classes
```

### With Spring IoC
```java
@Component
class PetrolEngine implements Engine {}

@Component
class Car {
    @Autowired
    Engine engine;
}

// Spring container creates objects
// Spring manages dependencies automatically
```
### IoC Containers

- **BeanFactory** – basic container
- **ApplicationContext** – advanced (recommended)

---

## 4. Dependency Injection (DI)

- Dependency Injection is a design principle where objects do not create their own dependencies.
- Instead, Spring container injects the required objects at runtime.
- 👉 This promotes loose coupling, easy testing, and better maintainability.

### Types of Dependency Injection 

- Constructor Injection ✅ (Best practice)
- Setter Injection
- Field Injection (Not recommended for testing)


### Problem without Dependency Injection (Tight Coupling)

### Example – Constructor Injection

```java
class Engine {
    public void start() {
        System.out.println("Engine started");
    }
}

class Car {
    private Engine engine = new Engine(); // tightly coupled

    public void drive() {
        engine.start();
        System.out.println("Car is running");
    }
}

```
❌ Problems:

- Car is tightly coupled to Engine
- Difficult to replace Engine or test Car

### How Dependency Injection (Loose Coupling) solve it ?

### Step 1: Create Interface
```java
public interface Engine {
    void start();
}
```
### Step 2: Implement Interface
```java
@Component
public class PetrolEngine implements Engine {
    public void start() {
        System.out.println("Petrol Engine started");
    }
}
```
### Step 3: Inject Dependency using Constructor Injection (Recommended)
```java
@Component
public class Car {

    private final Engine engine;

    @Autowired
    public Car(Engine engine) {
        this.engine = engine;
    }

    public void drive() {
        engine.start();
        System.out.println("Car is running");
    }
}
```
### Advantages of DI

- Loose coupling between classes
- Easy unit testing (mock dependencies)
- Better code maintainability
- Easy to switch implementations



---

## What are Spring Modules?

- **#1 Core Container** – Provides IoC and Dependency Injection.
- **#2 AOP Module** – Handles cross-cutting concerns like logging and security.
- **#3 Data Access Module** – Simplifies JDBC, ORM (Hibernate/JPA), and transactions
- **#4 Web Module** – Used to build web and REST applications (Spring MVC, WebFlux).
- **#5 Security & Test Modules** – Provides authentication, authorization, and testing support.

```sql
+--------------------------------------------------+
|                 Spring Framework                 |
+--------------------------------------------------+
|  Core Container                                  |
|  - Core | Beans | Context | SpEL                 |
+--------------------------------------------------+
|  AOP & Aspects                                   |
|  - Spring AOP | Spring Aspects                   |
+--------------------------------------------------+
|  Data Access / Integration                       |
|  - JDBC | ORM (Hibernate/JPA) | Transactions     |
+--------------------------------------------------+
|  Web                                            |
|  - Spring MVC | Spring Web | WebFlux             |
+--------------------------------------------------+
|  Security & Testing                              |
|  - Spring Security | Spring Test                 |
+--------------------------------------------------+
```
<img width="729" height="385" alt="image" src="https://github.com/user-attachments/assets/ad64013d-30df-480d-ac38-55726c440f5d" />


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
