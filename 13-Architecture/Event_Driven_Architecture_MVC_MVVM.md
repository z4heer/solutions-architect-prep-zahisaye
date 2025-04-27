# 🧠 Event-Driven Architecture, MVC, MVVM - Mind Map

---

## 🎯 Event-Driven Architecture (EDA)
- Producers ➔ Event Emitters
- Consumers ➔ Event Handlers
- Event Bus ➔ Manages Events Flow (e.g., Kafka, RabbitMQ)

---

## 📚 MVC (Model-View-Controller)
- **Model** ➔ Business logic/data.
- **View** ➔ UI layer.
- **Controller** ➔ Interaction handler.

---

## 📚 MVVM (Model-View-ViewModel)
- **Model** ➔ Business logic/data.
- **View** ➔ UI layer.
- **ViewModel** ➔ Binds Model & View, exposes observable data.

---

## 🔹 Key Technical Words
- **Event Streaming**: Continuous event flow (Kafka, Pulsar).
- **Publisher/Subscriber**: Messaging pattern.

---

## 🛠️ Best Practices
- Ensure idempotency in consumers.
- Use schemas for events (Avro, JSON Schema).
- MVC/MVVM ➔ Separate concerns cleanly.

---

## ❓ Interview Questions
- How would you implement an Event-Driven System?
- MVC vs MVVM - when to choose?

---

## 📋 Cheat Sheet
| Concept | Benefit |
|:---|:---|
| MVC | Separation of Concerns |
| MVVM | Easier Data Binding |
| EDA | Scalability & Flexibility |

---

## ⚡ Common Mistakes
- Tight coupling between producers and consumers.
- No clear error handling on event failure.

---
