# 📚 Microservices Architecture

**Microservices Architecture** is an architectural style that structures an application as a collection of loosely coupled services, which implement business capabilities. Each microservice is independently deployable, scalable, and has its own database.

---

## 🧠 Mind Map

```
Microservices Architecture
├── Definition
├── Characteristics
│   ├── Loose Coupling
│   ├── High Cohesion
│   ├── Independent Deployability
│   └── Decentralized Data Management
├── Advantages
├── Disadvantages
├── Real-world Examples
├── Key Components
│   ├── API Gateway
│   ├── Service Discovery
│   ├── Database per Service
│   └── Inter-Service Communication
``` 

---

## 📚 Key Technical Words & Definitions

| Term | Definition |
|------|------------|
| **Microservice** | A small, independently deployable service focused on a specific business capability. |
| **API Gateway** | A single entry point for all client requests, often handling routing, authentication, and rate limiting. |
| **Service Discovery** | The process of locating services within a microservices architecture, enabling dynamic communication. |
| **Database per Service** | Each microservice has its own database to ensure loose coupling and scalability. |
| **Inter-Service Communication** | Mechanisms for communication between microservices, such as HTTP, gRPC, or messaging systems. |

---

## 🔎 Common Interview Questions

- What is Microservices Architecture and how is it different from monolithic architecture?
- What are the main challenges in a microservices-based application?
- How do you handle inter-service communication in a microservices architecture?
- Can you explain the role of an API Gateway in a microservices environment?
- What are the benefits of using a decentralized database in microservices?
- How do you manage transactions in microservices?

---

## 🧪 Code Snippets

### Example: Spring Boot Microservice (Basic Setup)

```java
// Application Class (Main Class for Spring Boot Microservice)
package com.example.microservice;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class MicroserviceApplication {
    public static void main(String[] args) {
        SpringApplication.run(MicroserviceApplication.class, args);
    }
}
```

```java
// Controller for handling REST requests
package com.example.microservice.controller;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class MicroserviceController {
    
    @GetMapping("/hello")
    public String helloWorld() {
        return "Hello, Microservices!";
    }
}
```

---

## 🎯 Best Practices Summary

- ✅ Keep services small and focused on specific business functionalities.
- ✅ Use asynchronous messaging (e.g., Kafka, RabbitMQ) for inter-service communication to ensure scalability.
- ✅ Ensure that each microservice has its own independent database to avoid direct dependencies between services.
- ✅ Use centralized logging and monitoring tools like ELK Stack, Prometheus, or Grafana for observability.
- ✅ Implement CI/CD pipelines to automate deployment and scaling.

---

## 📘 Cheat Sheet Summary

| Concept | Usage |
|---------|-------|
| Microservices | Small, independent services that focus on specific business capabilities. |
| API Gateway | Manages and routes client requests to appropriate microservices. |
| Service Discovery | Allows microservices to find and communicate with each other dynamically. |
| Database per Service | Ensures each service has its own database for better scaling and loose coupling. |

---

## ⚠️ Common Mistakes

| Mistake | Why Avoid |
|---------|-----------|
| Overcomplicating microservices | Leads to unnecessary overhead, especially when not needed. |
| Not managing service communication properly | Can result in tight coupling and system failure in case of failure in communication. |
| Ignoring the complexity of deployment and monitoring | Microservices can be challenging to manage at scale if proper monitoring and deployment pipelines are not in place. |

---

## 🔗 Extras

- [Microservices Architecture - Martin Fowler](https://martinfowler.com/articles/microservices.html)
- [Microservices Design Patterns](https://www.enterpriseintegrationpatterns.com/)
- [Spring Boot Microservices Example](https://spring.io/guides/gs/microservice/)
