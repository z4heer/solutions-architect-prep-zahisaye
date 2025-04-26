# 📚 Spring Boot Key Terms

Spring Boot is a framework that simplifies the development of Java-based applications, providing production-ready features and reducing the complexity of configuration and deployment. Below are the key terms you should be familiar with when working with Spring Boot.

---

## 🧠 Mind Map

```
Spring Boot Key Terms
├── Definition
├── Core Concepts
│   ├── Auto Configuration
│   ├── Embedded Server
│   ├── Spring Boot Starter
│   ├── Spring Boot Actuator
│   └── Spring Boot CLI
├── Annotations
│   ├── @SpringBootApplication
│   ├── @RestController
│   └── @Value
├── Components
│   ├── ApplicationContext
│   ├── Bean
│   └── Component Scan
└── Common Use Cases
    ├── Building REST APIs
    ├── Database Integration
    └── Monitoring and Management
```

---

## 📚 Key Technical Words & Definitions

| Term | Definition |
|------|------------|
| **Auto Configuration** | Automatically configures application components based on the dependencies in the classpath. |
| **Embedded Server** | An internal web server (like Tomcat, Jetty, or Undertow) that allows Spring Boot applications to run as stand-alone applications without needing an external server. |
| **Spring Boot Starter** | Pre-configured set of dependencies that can be included to add specific functionality to the Spring Boot project (e.g., web, data, security). |
| **Spring Boot Actuator** | A set of production-ready features that help monitor and manage Spring Boot applications, such as health checks and metrics. |
| **Spring Boot CLI** | Command-line tool that helps you run Spring Boot applications from the terminal, providing quick prototypes and testing. |
| **@SpringBootApplication** | A combination of `@Configuration`, `@EnableAutoConfiguration`, and `@ComponentScan` annotations used to mark the main class for a Spring Boot application. |
| **@RestController** | A convenience annotation for `@Controller` and `@ResponseBody`, indicating a controller that handles HTTP requests and responses in RESTful applications. |
| **@Value** | Annotation used to inject values into Spring Beans, typically from properties or configuration files. |

---

## 🔎 Common Interview Questions

- What is Spring Boot and how does it simplify application development?
- Can you explain the role of Spring Boot Starters and give some examples?
- How does Spring Boot handle application configuration automatically?
- What is the difference between `@SpringBootApplication` and `@EnableAutoConfiguration`?
- How do you perform health checks and monitoring in a Spring Boot application?
- How can you create RESTful APIs with Spring Boot?

---

## 🧪 Code Snippets

### Example: Spring Boot Main Application Class

```java
package com.example.springboot;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}
```

### Example: Spring Boot REST Controller

```java
package com.example.springboot.controller;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {

    @GetMapping("/hello")
    public String sayHello() {
        return "Hello, Spring Boot!";
    }
}
```

---

## 🎯 Best Practices Summary

- ✅ Use Spring Boot Starters to quickly include commonly used dependencies.
- ✅ Leverage auto-configuration to simplify your project setup and reduce boilerplate code.
- ✅ Use Spring Boot Actuator for real-time monitoring and health checks in production environments.
- ✅ Always externalize configuration properties using `application.properties` or `application.yml`.
- ✅ Structure your Spring Boot application logically by following standard conventions for packages and classes.

---

## 📘 Cheat Sheet Summary

| Concept | Usage |
|---------|-------|
| **Spring Boot Starter** | A set of pre-configured dependencies for adding functionality to your app. |
| **@SpringBootApplication** | Annotation that simplifies Spring Boot setup. |
| **Auto Configuration** | Automatic configuration based on classpath dependencies. |
| **Spring Boot Actuator** | Provides production-ready features for monitoring and managing your application. |

---

## ⚠️ Common Mistakes

| Mistake | Why Avoid |
|---------|-----------|
| Not utilizing auto-configuration effectively | Leads to increased configuration and complexity. |
| Overloading the `@SpringBootApplication` class | Results in harder-to-maintain code and cluttered classes. |
| Hardcoding configuration values | Reduces flexibility and makes the application difficult to maintain. |

---

## 🔗 Extras

- [Spring Boot Documentation](https://docs.spring.io/spring-boot/docs/current/reference/html/)
- [Spring Boot Starter Guides](https://spring.io/guides)
- [Spring Boot Actuator - Reference Documentation](https://docs.spring.io/spring-boot/docs/current/reference/html/production-ready-features.html)
