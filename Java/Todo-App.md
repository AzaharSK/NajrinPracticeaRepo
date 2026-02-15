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

-------------------------------------------

##  Entity Layer :


__entity/Role.java__

```java
package com.todo.entity;

public enum Role {
    ROLE_ADMIN,
    ROLE_USER
}
```
__entity/User.java__

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

__entity/Todo.java__

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
------------------------------------
## DTO LAYER

__dto/LoginRequest.java__

```java
package com.todo.dto;

import jakarta.validation.constraints.NotBlank;
import lombok.Data;

@Data
public class LoginRequest {
    @NotBlank
    private String username;

    @NotBlank
    private String password;
}
```

__dto/RegisterRequest.java__

```java
package com.todo.dto;

import jakarta.validation.constraints.NotBlank;
import lombok.Data;

@Data
public class RegisterRequest {

    @NotBlank
    private String username;

    @NotBlank
    private String password;
}
```

__dto/TodoDto.java__

```java
package com.todo.dto;

import jakarta.validation.constraints.NotBlank;
import lombok.Data;

@Data
public class TodoDto {

    @NotBlank
    private String title;

    private String description;
    private boolean completed;
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
import org.springframework.stereotype.Component;

import java.security.Key;
import java.util.Date;

@Component
public class JwtUtil {

    private final String SECRET = "verysecretkeyverysecretkeyverysecretkey123";
    private final long EXPIRATION = 1000 * 60 * 60 * 24;

    private final Key key = Keys.hmacShaKeyFor(SECRET.getBytes());

    public String generateToken(String username, String role) {

        return Jwts.builder()
                .setSubject(username)
                .claim("role", role)
                .setIssuedAt(new Date())
                .setExpiration(new Date(System.currentTimeMillis() + EXPIRATION))
                .signWith(key)
                .compact();
    }

    public String extractUsername(String token) {
        return getClaims(token).getSubject();
    }

    public String extractRole(String token) {
        return getClaims(token).get("role", String.class);
    }

    public boolean isValid(String token) {
        try {
            getClaims(token);
            return true;
        } catch (JwtException e) {
            return false;
        }
    }

    private Claims getClaims(String token) {
        return Jwts.parserBuilder()
                .setSigningKey(key)
                .build()
                .parseClaimsJws(token)
                .getBody();
    }
}

```

__security/JwtFilter.java__

```java

package com.todo.security;

import jakarta.servlet.FilterChain;
import jakarta.servlet.ServletException;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

import lombok.RequiredArgsConstructor;

import org.springframework.http.HttpHeaders;
import org.springframework.security.authentication.UsernamePasswordAuthenticationToken;
import org.springframework.security.core.context.SecurityContextHolder;
import org.springframework.security.core.userdetails.UserDetails;
import org.springframework.security.web.authentication.WebAuthenticationDetailsSource;
import org.springframework.stereotype.Component;
import org.springframework.web.filter.OncePerRequestFilter;

import java.io.IOException;

@Component
@RequiredArgsConstructor
public class JwtFilter extends OncePerRequestFilter {

    private final JwtUtil jwtUtil;
    private final CustomUserDetailsService userDetailsService;

    @Override
    protected void doFilterInternal(HttpServletRequest request,
                                    HttpServletResponse response,
                                    FilterChain filterChain)
            throws ServletException, IOException {

        try {

            String header = request.getHeader(HttpHeaders.AUTHORIZATION);

            // No token → continue (public endpoints may still work)
            if (header == null || !header.startsWith("Bearer ")) {
                filterChain.doFilter(request, response);
                return;
            }

            String token = header.substring(7);

            // Invalid token → continue but no auth
            if (!jwtUtil.isValid(token)) {
                filterChain.doFilter(request, response);
                return;
            }

            String username = jwtUtil.extractUsername(token);

            // If already authenticated, skip
            if (username != null && SecurityContextHolder.getContext().getAuthentication() == null) {

                UserDetails userDetails = userDetailsService.loadUserByUsername(username);

                UsernamePasswordAuthenticationToken authToken =
                        new UsernamePasswordAuthenticationToken(
                                userDetails,
                                null,
                                userDetails.getAuthorities()
                        );

                authToken.setDetails(new WebAuthenticationDetailsSource().buildDetails(request));

                SecurityContextHolder.getContext().setAuthentication(authToken);
            }

        } catch (Exception ex) {
            // Important: clear context if token parsing fails
            SecurityContextHolder.clearContext();
        }

        filterChain.doFilter(request, response);
    }
}
```


## security/SecurityConfig.java

```java
package com.todo.security;

import lombok.RequiredArgsConstructor;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.http.HttpMethod;

import org.springframework.security.authentication.AuthenticationManager;
import org.springframework.security.config.annotation.authentication.configuration.AuthenticationConfiguration;

import org.springframework.security.config.annotation.method.configuration.EnableMethodSecurity;
import org.springframework.security.config.http.SessionCreationPolicy;

import org.springframework.security.crypto.bcrypt.BCryptPasswordEncoder;
import org.springframework.security.crypto.password.PasswordEncoder;

import org.springframework.security.web.AuthenticationEntryPoint;
import org.springframework.security.web.SecurityFilterChain;
import org.springframework.security.web.access.AccessDeniedHandler;
import org.springframework.security.web.authentication.UsernamePasswordAuthenticationFilter;

import org.springframework.security.config.annotation.web.builders.HttpSecurity;

import jakarta.servlet.http.HttpServletResponse;

@Configuration
@EnableMethodSecurity
@RequiredArgsConstructor
public class SecurityConfig {

    private final JwtFilter jwtFilter;

    // ================= PASSWORD ENCODER =================
    @Bean
    public PasswordEncoder passwordEncoder() {
        return new BCryptPasswordEncoder();
    }

    // ================= AUTH MANAGER =================
    @Bean
    public AuthenticationManager authenticationManager(AuthenticationConfiguration config) throws Exception {
        return config.getAuthenticationManager();
    }

    // ================= 401 HANDLER =================
    @Bean
    public AuthenticationEntryPoint unauthorizedHandler() {
        return (request, response, ex) ->
                response.sendError(HttpServletResponse.SC_UNAUTHORIZED, "Unauthorized: Invalid or missing token");
    }

    // ================= 403 HANDLER =================
    @Bean
    public AccessDeniedHandler accessDeniedHandler() {
        return (request, response, ex) ->
                response.sendError(HttpServletResponse.SC_FORBIDDEN, "Forbidden: You don't have permission");
    }

    // ================= SECURITY FILTER CHAIN =================
    @Bean
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {

        http
            // Disable CSRF for REST API
            .csrf(csrf -> csrf.disable())

            // Stateless session (JWT)
            .sessionManagement(session ->
                    session.sessionCreationPolicy(SessionCreationPolicy.STATELESS)
            )

            // Exception handling
            .exceptionHandling(ex -> ex
                    .authenticationEntryPoint(unauthorizedHandler())
                    .accessDeniedHandler(accessDeniedHandler())
            )

            // Authorization rules
            .authorizeHttpRequests(auth -> auth

                    // PUBLIC ENDPOINTS
                    .requestMatchers("/api/auth/**").permitAll()
                    .requestMatchers("/h2-console/**").permitAll()

                    // ADMIN ONLY
                    .requestMatchers("/api/admin/**").hasRole("ADMIN")

                    // TODOS — logged in users
                    .requestMatchers(HttpMethod.GET, "/api/todos/**").hasAnyRole("USER","ADMIN")
                    .requestMatchers(HttpMethod.POST, "/api/todos/**").hasAnyRole("USER","ADMIN")
                    .requestMatchers(HttpMethod.PUT, "/api/todos/**").hasAnyRole("USER","ADMIN")
                    .requestMatchers(HttpMethod.DELETE, "/api/todos/**").hasAnyRole("USER","ADMIN")

                    // everything else
                    .anyRequest().authenticated()
            )

            // Add JWT filter
            .addFilterBefore(jwtFilter, UsernamePasswordAuthenticationFilter.class);

        // For H2 console
        http.headers(headers -> headers.frameOptions(frame -> frame.disable()));

        return http.build();
    }
}

```

-----------------------------------------------------------

## 🧩 SERVICE LAYER :

__service/AuthService.java__

```java
package com.todo.service;

import com.todo.dto.LoginRequest;
import com.todo.dto.RegisterRequest;
import com.todo.entity.Role;
import com.todo.entity.User;
import com.todo.repository.UserRepository;
import com.todo.security.JwtUtil;
import lombok.RequiredArgsConstructor;
import org.springframework.security.crypto.password.PasswordEncoder;
import org.springframework.stereotype.Service;

@Service
@RequiredArgsConstructor
public class AuthService {

    private final UserRepository userRepo;
    private final PasswordEncoder encoder;
    private final JwtUtil jwt;

    public String register(RegisterRequest req) {

        if (userRepo.findByUsername(req.getUsername()).isPresent())
            throw new RuntimeException("Username already exists");

        User user = new User();
        user.setUsername(req.getUsername());
        user.setPassword(encoder.encode(req.getPassword()));
        user.setRole(Role.ROLE_USER);

        userRepo.save(user);

        return "User registered successfully";
    }

    public String login(LoginRequest req) {

        User user = userRepo.findByUsername(req.getUsername())
                .orElseThrow(() -> new RuntimeException("User not found"));

        if (!encoder.matches(req.getPassword(), user.getPassword()))
            throw new RuntimeException("Invalid password");

        return jwt.generateToken(user.getUsername(), user.getRole().name());
    }
}

```

__service/UserService.java (ADMIN ONLY OPERATIONS)__

```java
package com.todo.service;

import com.todo.entity.User;
import com.todo.repository.UserRepository;
import lombok.RequiredArgsConstructor;
import org.springframework.stereotype.Service;

import java.util.List;

@Service
@RequiredArgsConstructor
public class UserService {

    private final UserRepository repo;

    // ADMIN: View all users
    public List<User> getAllUsers() {
        return repo.findAll();
    }

    // ADMIN: Delete user
    public void deleteUser(Long id) {

        User user = repo.findById(id)
                .orElseThrow(() -> new RuntimeException("User not found"));

        repo.delete(user);
    }

    // ADMIN: Change role
    public User changeRole(Long id, String role) {

        User user = repo.findById(id)
                .orElseThrow(() -> new RuntimeException("User not found"));

        user.setRole(Enum.valueOf(com.todo.entity.Role.class, role));

        return repo.save(user);
    }
}
```

__service/TodoService.java (OWNERSHIP SECURITY 🔥)__

```java
package com.todo.service;

import com.todo.dto.TodoDto;
import com.todo.entity.Todo;
import com.todo.entity.User;
import com.todo.repository.TodoRepository;
import com.todo.repository.UserRepository;
import lombok.RequiredArgsConstructor;
import org.springframework.security.core.context.SecurityContextHolder;
import org.springframework.stereotype.Service;

import java.util.List;

@Service
@RequiredArgsConstructor
public class TodoService {

    private final TodoRepository todoRepo;
    private final UserRepository userRepo;

    private User currentUser() {
        String username = SecurityContextHolder.getContext().getAuthentication().getName();
        return userRepo.findByUsername(username)
                .orElseThrow(() -> new RuntimeException("User not found"));
    }

    // CREATE
    public Todo create(TodoDto dto) {

        Todo todo = new Todo();
        todo.setTitle(dto.getTitle());
        todo.setDescription(dto.getDescription());
        todo.setCompleted(false);
        todo.setUser(currentUser());

        return todoRepo.save(todo);
    }

    // READ MY TODOS
    public List<Todo> myTodos() {
        return todoRepo.findByUserId(currentUser().getId());
    }

    // UPDATE (only owner)
    public Todo update(Long id, TodoDto dto) {

        Todo todo = todoRepo.findById(id)
                .orElseThrow(() -> new RuntimeException("Todo not found"));

        if (!todo.getUser().getId().equals(currentUser().getId()))
            throw new RuntimeException("You cannot edit others todos");

        todo.setTitle(dto.getTitle());
        todo.setDescription(dto.getDescription());
        todo.setCompleted(dto.isCompleted());

        return todoRepo.save(todo);
    }

    // DELETE (only owner)
    public void delete(Long id) {

        Todo todo = todoRepo.findById(id)
                .orElseThrow(() -> new RuntimeException("Todo not found"));

        if (!todo.getUser().getId().equals(currentUser().getId()))
            throw new RuntimeException("You cannot delete others todos");

        todoRepo.delete(todo);
    }
}
```

----------------------------------------------------------------------


## 🌐 CONTROLLERS

```java
controller/AuthController.java
package com.todo.controller;

import com.todo.dto.LoginRequest;
import com.todo.dto.RegisterRequest;
import com.todo.service.AuthService;
import jakarta.validation.Valid;
import lombok.RequiredArgsConstructor;
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/api/auth")
@RequiredArgsConstructor
public class AuthController {

    private final AuthService service;

    @PostMapping("/register")
    public String register(@Valid @RequestBody RegisterRequest req) {
        return service.register(req);
    }

    @PostMapping("/login")
    public String login(@Valid @RequestBody LoginRequest req) {
        return service.login(req);
    }
}
```

## controller/UserController.java (ADMIN PROTECTED)

```java
package com.todo.controller;

import com.todo.entity.User;
import com.todo.service.UserService;
import lombok.RequiredArgsConstructor;
import org.springframework.security.access.prepost.PreAuthorize;
import org.springframework.web.bind.annotation.*;

import java.util.List;

@RestController
@RequestMapping("/api/admin/users")
@RequiredArgsConstructor
@PreAuthorize("hasRole('ADMIN')")
public class UserController {

    private final UserService service;

    @GetMapping
    public List<User> allUsers() {
        return service.getAllUsers();
    }

    @DeleteMapping("/{id}")
    public void delete(@PathVariable Long id) {
        service.deleteUser(id);
    }

    @PutMapping("/{id}/role")
    public User changeRole(@PathVariable Long id, @RequestParam String role) {
        return service.changeRole(id, role);
    }
}
```

__controller/TodoController.java__

```
package com.todo.controller;

import com.todo.dto.TodoDto;
import com.todo.entity.Todo;
import com.todo.service.TodoService;
import jakarta.validation.Valid;
import lombok.RequiredArgsConstructor;
import org.springframework.web.bind.annotation.*;

import java.util.List;

@RestController
@RequestMapping("/api/todos")
@RequiredArgsConstructor
public class TodoController {

    private final TodoService service;

    @PostMapping
    public Todo create(@Valid @RequestBody TodoDto dto) {
        return service.create(dto);
    }

    @GetMapping
    public List<Todo> myTodos() {
        return service.myTodos();
    }

    @PutMapping("/{id}")
    public Todo update(@PathVariable Long id, @RequestBody TodoDto dto) {
        return service.update(id, dto);
    }

    @DeleteMapping("/{id}")
    public void delete(@PathVariable Long id) {
        service.delete(id);
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
