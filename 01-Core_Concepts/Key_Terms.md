# 📚 Core Concepts Key Terms

Core concepts in programming, design, and architecture provide the foundation for building scalable, efficient, and maintainable systems. This document covers key terms related to fundamental concepts that every Solutions Architect or developer should be familiar with.

---

## 🧠 Mind Map

```
Core Concepts Key Terms
├── Design Patterns
│   ├── Singleton
│   ├── Factory
│   └── Observer
├── SOLID Principles
│   ├── Single Responsibility
│   ├── Open/Closed
│   ├── Liskov Substitution
│   ├── Interface Segregation
│   └── Dependency Inversion
├── Architecture Styles
│   ├── Monolithic
│   ├── Microservices
│   └── Serverless
├── Data Structures
│   ├── Array
│   ├── Linked List
│   └── HashMap
├── Algorithms
│   ├── Sorting
│   ├── Searching
│   └── Graph Traversal
└── Performance Optimization
    ├── Caching
    ├── Load Balancing
    └── Asynchronous Processing
```

---

## 📚 Key Technical Words & Definitions

| Term | Definition |
|------|------------|
| **Singleton** | A design pattern that ensures a class has only one instance and provides a global point of access to that instance. |
| **Factory Pattern** | A design pattern used to create objects without specifying the exact class of object that will be created. |
| **Observer Pattern** | A behavioral design pattern where one object (subject) maintains a list of dependent objects (observers) that need to be notified of state changes. |
| **SOLID Principles** | A set of five design principles that make software designs more understandable, flexible, and maintainable. |
| **Monolithic Architecture** | A software architecture pattern where all components are tightly integrated and run as a single unit. |
| **Microservices Architecture** | A pattern where an application is broken down into a set of loosely coupled, independently deployable services. |
| **Serverless Architecture** | A cloud-native architecture where developers write functions, and the cloud provider takes care of the execution environment. |
| **Array** | A data structure that stores a collection of items of the same type, arranged in contiguous memory locations. |
| **Linked List** | A linear data structure where each element points to the next, allowing for efficient insertion and deletion of elements. |
| **HashMap** | A data structure that stores key-value pairs, allowing for fast retrieval based on the key. |
| **Caching** | The practice of storing frequently accessed data in memory to reduce access time and improve performance. |
| **Load Balancing** | The distribution of incoming network traffic across multiple servers to ensure high availability and reliability. |
| **Asynchronous Processing** | A method of processing tasks where the system does not wait for the task to complete before moving on to the next task. |

---

## 🔎 Common Interview Questions

- What is the Singleton pattern, and how does it ensure only one instance of a class is created?
- Can you explain the Factory pattern and provide a scenario where it can be used effectively?
- What is the Observer pattern, and when would you use it?
- How does the SOLID principle improve code quality? Can you explain each of the SOLID principles?
- What is the difference between Monolithic, Microservices, and Serverless architectures?
- How do you implement efficient searching and sorting algorithms? What are their time complexities?
- Can you explain the importance of performance optimization in large-scale systems? How do you implement caching?

---

## 🧪 Code Snippets

### Example: Singleton Pattern

```java
public class Singleton {

    // Step 1: Create a static instance of the class
    private static Singleton instance;

    // Step 2: Make the constructor private to prevent instantiation
    private Singleton() {}

    // Step 3: Provide a public method to get the instance
    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

### Example: Factory Pattern

```java
public abstract class Animal {
    public abstract void sound();
}

public class Dog extends Animal {
    public void sound() {
        System.out.println("Bark");
    }
}

public class Cat extends Animal {
    public void sound() {
        System.out.println("Meow");
    }
}

public class AnimalFactory {
    public static Animal createAnimal(String type) {
        if (type.equals("dog")) {
            return new Dog();
        } else if (type.equals("cat")) {
            return new Cat();
        }
        return null;
    }
}
```

### Example: Load Balancer

```java
import java.util.List;
import java.util.Random;

public class LoadBalancer {

    private List<String> servers;

    public LoadBalancer(List<String> servers) {
        this.servers = servers;
    }

    public String getNextServer() {
        Random random = new Random();
        return servers.get(random.nextInt(servers.size()));
    }
}
```

---

## 🎯 Best Practices Summary

- ✅ Follow **SOLID principles** to make your code more maintainable and extensible.
- ✅ Use design patterns like **Singleton**, **Factory**, and **Observer** to solve common problems in a flexible way.
- ✅ Consider **Microservices** or **Serverless** architecture for scalable and fault-tolerant applications.
- ✅ Choose appropriate **data structures** based on the use case to improve performance and memory efficiency.
- ✅ Always optimize for **performance** with techniques like caching and load balancing.

---

## 📘 Cheat Sheet Summary

| Concept | Usage |
|---------|-------|
| **Singleton** | Ensures a class has only one instance, used for logging, configuration, etc. |
| **Factory Pattern** | Use when you need to create objects but don’t want to expose the logic to the client. |
| **Observer Pattern** | Ideal for implementing event-driven architectures where multiple components need to react to changes. |
| **Monolithic** | Best for small applications or when rapid development is required. |
| **Microservices** | Use when scalability, fault tolerance, and independent deployment are priorities. |
| **Serverless** | Use for event-driven, stateless applications to minimize infrastructure management. |

---

## ⚠️ Common Mistakes

| Mistake | Why Avoid |
|---------|-----------|
| Ignoring SOLID principles | Leads to rigid, hard-to-maintain, and error-prone code. |
| Overusing the Singleton pattern | Makes code difficult to test and leads to tightly coupled code. |
| Choosing the wrong architecture style | Leads to inefficiency or complexity that isn't required for the use case. |

---

## 🔗 Extras

- [Design Patterns Documentation](https://refactoring.guru/design-patterns)
- [SOLID Principles Explanation](https://www.solidprinciples.com)
- [Microservices vs Monolithic Architecture](https://www.martinfowler.com/articles/microservices.html)
