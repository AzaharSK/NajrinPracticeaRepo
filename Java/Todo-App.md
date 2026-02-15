# TODO Management Full-Stack Application :

## 🏗 1. Architecture Overview

- __`Tech Stack`__

- `Backend:` Spring Boot 3.x
- `Security:` Spring Security + JWT + OAuth2
- `DB (Test):` H2
- `DB (Prod):` MySQL (Azure Database for MySQL)
- `Frontend:` React
- `DevOps:` Docker, Azure DevOps
- `Cloud:` Azure App Service

```scss
React (Azure App Service Static Web App)
        ↓
Spring Boot REST API (Azure App Service / Docker)
        ↓
Azure Database for MySQL (Prod)
H2 (Test profile)
```

## 🔹 2. Backend – Spring Boot REST API

- Step 1: Create Project
- Use Spring Initializr:

Dependencies:

- Spring Web
- Spring Data JPA
- Spring Security
- OAuth2 Resource Server
- MySQL Driver
- H2
- Lombok
- Validation
- Flyway (for migration)
- Docker Support


## 📁 Project Structure

```
todo-fullstack/
│
├── backend/
│   ├── pom.xml
│   ├── Dockerfile
│   └── src/main/java/com/todo/
│       ├── TodoApplication.java
│       ├── entity/
│       │   ├── User.java
│       │   ├── Role.java
│       │   └── Todo.java
│       ├── repository/
│       │   ├── UserRepository.java
│       │   └── TodoRepository.java
│       ├── service/
│       │   ├── AuthService.java
│       │   ├── UserService.java
│       │   └── TodoService.java
│       ├── controller/
│       │   ├── AuthController.java
│       │   ├── UserController.java
│       │   └── TodoController.java
│       ├── security/
│       │   ├── JwtUtil.java
│       │   ├── JwtFilter.java
│       │   └── SecurityConfig.java
│       ├── dto/
│       │   ├── LoginRequest.java
│       │   ├── RegisterRequest.java
│       │   └── TodoDto.java
│       └── exception/
│           └── GlobalExceptionHandler.java
│
│   └── src/main/resources/
│       ├── application.yml
│       └── db/migration/V1__init.sql
│
└── frontend/
    ├── package.json
    └── src/
        ├── App.js
        ├── api.js
        ├── Login.js
        ├── Register.js
        ├── Dashboard.js
        └── AdminPanel.js

```

=========================
🔵 BACKEND SOURCE CODE
=========================

## backend/pom.xml

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.todo</groupId>
    <artifactId>todo</artifactId>
    <version>0.0.1</version>
    <packaging>jar</packaging>

    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>3.2.0</version>
    </parent>

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-security</artifactId>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-jpa</artifactId>
        </dependency>

        <dependency>
            <groupId>io.jsonwebtoken</groupId>
            <artifactId>jjwt-api</artifactId>
            <version>0.11.5</version>
        </dependency>

        <dependency>
            <groupId>io.jsonwebtoken</groupId>
            <artifactId>jjwt-impl</artifactId>
            <scope>runtime</scope>
            <version>0.11.5</version>
        </dependency>

        <dependency>
            <groupId>io.jsonwebtoken</groupId>
            <artifactId>jjwt-jackson</artifactId>
            <scope>runtime</scope>
            <version>0.11.5</version>
        </dependency>

        <dependency>
            <groupId>com.h2database</groupId>
            <artifactId>h2</artifactId>
        </dependency>

        <dependency>
            <groupId>com.mysql</groupId>
            <artifactId>mysql-connector-j</artifactId>
        </dependency>

        <dependency>
            <groupId>org.flywaydb</groupId>
            <artifactId>flyway-core</artifactId>
        </dependency>

        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
        </dependency>
    </dependencies>
</project>
```
## entity/Role.java

```java
package com.todo.entity;

public enum Role {
    ROLE_ADMIN,
    ROLE_USER
}
```
## entity/User.java
```java
package com.todo.entity;

import jakarta.persistence.*;
import lombok.*;

@Entity
@Table(name = "users")
@Getter @Setter
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(unique = true)
    private String username;

    private String password;

    @Enumerated(EnumType.STRING)
    private Role role;
}
```


## entity/Todo.java

```java
package com.todo.entity;

import jakarta.persistence.*;
import lombok.*;

@Entity
@Getter @Setter
public class Todo {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String title;
    private String description;
    private boolean completed;

    @ManyToOne
    private User user;
}

```

## package com.todo.repository;

```java

import org.springframework.data.jpa.repository.JpaRepository;
import com.todo.entity.User;
import java.util.Optional;

public interface UserRepository extends JpaRepository<User, Long> {
    Optional<User> findByUsername(String username);
}

```

## security/JwtUtil.java

```
package com.todo.security;

import io.jsonwebtoken.*;
import io.jsonwebtoken.security.Keys;
import java.util.Date;
import java.security.Key;

public class JwtUtil {

    private static final String SECRET = "verysecretkeyverysecretkey123456";
    private static final Key key = Keys.hmacShaKeyFor(SECRET.getBytes());

    public static String generateToken(String username) {
        return Jwts.builder()
                .setSubject(username)
                .setExpiration(new Date(System.currentTimeMillis() + 86400000))
                .signWith(key)
                .compact();
    }

    public static String extractUsername(String token) {
        return Jwts.parserBuilder().setSigningKey(key)
                .build().parseClaimsJws(token)
                .getBody().getSubject();
    }
}

```

## security/SecurityConfig.java

```java
package com.todo.security;

import org.springframework.context.annotation.*;
import org.springframework.security.config.annotation.method.configuration.EnableMethodSecurity;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.web.SecurityFilterChain;

@Configuration
@EnableMethodSecurity
public class SecurityConfig {

    @Bean
    SecurityFilterChain filterChain(HttpSecurity http) throws Exception {

        http.csrf(csrf -> csrf.disable())
            .authorizeHttpRequests(auth -> auth
                .requestMatchers("/api/auth/**").permitAll()
                .anyRequest().authenticated()
            );

        return http.build();
    }
}

```

## controller/AuthController.java

```java
package com.todo.controller;

import org.springframework.web.bind.annotation.*;
import com.todo.entity.*;
import com.todo.repository.*;
import com.todo.security.JwtUtil;
import lombok.RequiredArgsConstructor;
import org.springframework.security.crypto.bcrypt.BCryptPasswordEncoder;

@RestController
@RequestMapping("/api/auth")
@RequiredArgsConstructor
public class AuthController {

    private final UserRepository userRepo;
    private final BCryptPasswordEncoder encoder = new BCryptPasswordEncoder();

    @PostMapping("/register")
    public String register(@RequestBody User user) {
        user.setPassword(encoder.encode(user.getPassword()));
        user.setRole(Role.ROLE_USER);
        userRepo.save(user);
        return "User Registered";
    }

    @PostMapping("/login")
    public String login(@RequestBody User user) {
        User dbUser = userRepo.findByUsername(user.getUsername())
                .orElseThrow();
        if (encoder.matches(user.getPassword(), dbUser.getPassword())) {
            return JwtUtil.generateToken(user.getUsername());
        }
        throw new RuntimeException("Invalid credentials");
    }
}
```

## application.yml
```
spring:
  datasource:
    url: jdbc:h2:mem:testdb
    driver-class-name: org.h2.Driver
    username: sa
  h2:
    console:
      enabled: true
  jpa:
    hibernate:
      ddl-auto: update
  ```


## Dockerfile

```Dockerfile
FROM eclipse-temurin:17-jdk
COPY target/todo-0.0.1.jar app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
```

=========================
🟢 FRONTEND SOURCE CODE
=========================

## frontend/package.json

```json
{
  "name": "todo-ui",
  "version": "1.0.0",
  "dependencies": {
    "axios": "^1.6.0",
    "react-router-dom": "^6.0.0"
  }
}
```

## src/api.js

```java
import axios from "axios";

const api = axios.create({
  baseURL: "http://localhost:8080/api"
});

api.interceptors.request.use(config => {
  const token = localStorage.getItem("token");
  if(token) config.headers.Authorization = `Bearer ${token}`;
  return config;
});

export default api;

```

## src/Login.js

```
import api from "./api";
import { useState } from "react";

function Login() {
  const [username,setUsername]=useState("");
  const [password,setPassword]=useState("");

  const login = async () => {
    const res = await api.post("/auth/login",{username,password});
    localStorage.setItem("token",res.data);
  };

  return (
    <>
      <input onChange={e=>setUsername(e.target.value)} />
      <input type="password" onChange={e=>setPassword(e.target.value)} />
      <button onClick={login}>Login</button>
    </>
  );
}
export default Login;

```

## 🚀 AZURE DEPLOYMENT STEPS
__1️⃣ Create MySQL__
- Use: Azure Database for MySQL

__2️⃣ Deploy Backend__
- Use: Azure App Service

```
az webapp up --name todo-backend --runtime "JAVA:17"
```

__3️⃣ Setup CI/CD__

- Use: Azure DevOps

__Create pipeline:__

- Build
- Test
- Docker build
- Push to Azure Container Registry
- Deploy to App Service

##################################################

## 🔹 3. Database Design:
🧾 User Entity

```java
@Entity
@Table(name = "users")
@Getter @Setter
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(unique = true)
    private String username;

    private String password;

    @Enumerated(EnumType.STRING)
    private Role role;
}

public enum Role {
    ROLE_ADMIN,
    ROLE_USER
}

```



## 📝 Todo Entity:

```java

@Entity
public class Todo {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String title;
    private String description;
    private boolean completed;

    @ManyToOne
    private User user;
}
```
