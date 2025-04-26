# Architectural Design Patterns

Essential architectural patterns used in modern software systems for scalability, maintainability, and resilience.

---

## 🧠 Mind Map

- **Monolithic Architecture**
- **Microservices Architecture**
- **Event-Driven Architecture**
- **Serverless Architecture**
- **Layered (N-Tier) Architecture**
- **Hexagonal (Ports and Adapters) Architecture**
- **Service-Oriented Architecture (SOA)**
- **CQRS + Event Sourcing**

---

## 🎯 Key Technical Words & Definitions

| Pattern | Definition |
|:--------|:-----------|
| Monolithic Architecture | Single codebase application; tightly coupled components. |
| Microservices Architecture | Independently deployable services focusing on business capabilities. |
| Event-Driven Architecture | Components communicate by emitting and responding to events. |
| Serverless Architecture | Functions executed in cloud-managed environments (e.g., AWS Lambda). |
| Layered Architecture | Organizes code into layers: Presentation, Business, Data. |
| Hexagonal Architecture | Decouple core logic from external systems via Ports and Adapters. |
| Service-Oriented Architecture | Coarse-grained services interact over enterprise service bus. |
| CQRS | Separate Read and Write models for scalability and performance. |
| Event Sourcing | Store state changes as a sequence of events. |

---

## ❓ Common Interview Questions

- Compare and contrast Monolithic vs Microservices architectures.
- What is the benefit of Hexagonal architecture?
- How does Event Sourcing help in auditability and system recovery?
- When would you recommend Serverless over Microservices?
- How do you design for resilience in a distributed system?

---

## 🛠️ Code Snippet - Event-Driven Messaging (Spring Boot)

```java
@Service
public class OrderService {
    @Autowired
    private ApplicationEventPublisher publisher;

    public void createOrder(Order order) {
        // business logic
        publisher.publishEvent(new OrderCreatedEvent(this, order));
    }
}

public class OrderCreatedEvent extends ApplicationEvent {
    private final Order order;
    public OrderCreatedEvent(Object source, Order order) {
        super(source);
        this.order = order;
    }
}
```

---

## ✅ Best Practices Summary

- For small teams/projects, prefer monoliths initially and refactor later.
- Use Microservices when there’s a clear business/domain boundary and scaling needs.
- Implement Circuit Breakers, Retries, and Timeouts in distributed systems.
- Event sourcing adds complexity; apply where auditability is critical.

---

## 🚫 Common Mistakes

- Prematurely adopting Microservices leading to unnecessary complexity.
- Poor service boundary design causing high coupling between services.
- Ignoring observability (logging, tracing, monitoring) in distributed systems.
- Overusing Event-Driven architecture where simple synchronous calls suffice.

---

## 📋 Cheat Sheet Summary

| Architecture | When to Use |
|:-------------|:------------|
| Monolith | Early-stage products, fast iteration |
| Microservices | Independent scaling, multiple teams |
| Event-Driven | Asynchronous decoupling of services |
| Serverless | Event-driven, pay-as-you-go applications |
| CQRS + ES | Complex domains, auditability critical |

---

✅  
Next, ready to continue with **04-Patterns_And_Practices/Clean_Code_Principles.md**? 🚀
