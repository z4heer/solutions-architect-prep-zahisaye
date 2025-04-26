# Key Terms - Patterns and Practices

Important technical terms related to architecture patterns, clean code, best practices, and modern scalable software design.

---

## 🧠 Mind Map

- **Architecture** → Monolithic, Microservices, Serverless, Event-driven
- **Patterns** → Singleton, Factory, Strategy, CQRS, Saga
- **Principles** → SOLID, DRY, KISS, YAGNI, SRP
- **Practices** → CI/CD, TDD, DDD, Clean Architecture

---

## 🎯 Key Technical Words & Definitions

| Term | Definition |
|:-----|:------------|
| Monolithic Architecture | Single unified codebase/application. |
| Microservices Architecture | Distributed, independently deployable services. |
| Event-Driven Architecture | Systems that communicate asynchronously using events. |
| Singleton Pattern | Ensures a class has only one instance globally. |
| Factory Pattern | Creates objects without exposing instantiation logic. |
| Strategy Pattern | Enables selecting algorithms at runtime. |
| CQRS | Separates read and write operations for scalability. |
| SOLID Principles | Five design principles for better software maintainability. |
| CI/CD | Continuous Integration/Delivery for faster, reliable releases. |
| Domain-Driven Design (DDD) | Model complex software based on real-world domains. |
| Test-Driven Development (TDD) | Write tests before writing the functional code. |
| Clean Architecture | Layered architecture that separates concerns and dependencies. |

---

## ❓ Common Interview Questions

- What are the pros and cons of microservices vs monoliths?
- Explain the SOLID principles with examples.
- What is the Factory Design Pattern and when should it be used?
- How does event-driven architecture improve scalability?
- What are some trade-offs when applying DDD in a microservices environment?

---

## 🛠️ Code Snippet Example - Factory Pattern

```java
public interface Notification {
    void notifyUser();
}

public class EmailNotification implements Notification {
    public void notifyUser() {
        System.out.println("Sending Email Notification");
    }
}

public class NotificationFactory {
    public Notification createNotification(String type) {
        if ("EMAIL".equals(type)) {
            return new EmailNotification();
        }
        throw new IllegalArgumentException("Unknown type");
    }
}
```

---

## ✅ Best Practices Summary

- Always design for change (anticipate requirement changes).
- Prefer composition over inheritance.
- Favor clear, simple, and consistent designs over overengineering.
- Decouple components as much as possible for flexibility.

---

## 🚫 Common Mistakes

- Tight coupling between modules or layers.
- Ignoring scalability and observability early in the design.
- Misusing design patterns leading to unnecessary complexity.
- Lack of proper boundary definitions in microservices.

---

## 📋 Cheat Sheet Summary

| Best Practice | Key Reminder |
| :--- | :--- |
| SOLID | Maintainable & flexible code |
| DRY | No code duplication |
| YAGNI | Avoid overengineering |
| KISS | Keep It Simple, Stupid |
| Clean Architecture | Clear separation of concerns |

---

✅  
Next, we'll continue with **04-Patterns_And_Practices/Architectural_Design_Patterns.md**.  
Shall I proceed? 🚀
