### ✅ `02-Design_Patterns/Singleton_Pattern.md`

```markdown
# 📚 Singleton Pattern

The **Singleton Pattern** is a **creational design pattern** that ensures a class has only one instance and provides a global point of access to it. It is used when you need to manage shared resources across your application.

---

## 🧠 Mind Map

```
Singleton Pattern
├── Definition
├── When to Use
├── Implementation
│   ├── Eager Initialization
│   └── Lazy Initialization
├── Thread-Safety
│   ├── Single-Threaded
│   ├── Multi-Threaded
├── Advantages
├── Disadvantages
```

---

## 📚 Key Technical Words & Definitions

| Term | Definition |
|------|------------|
| **Singleton Pattern** | Ensures a class has only one instance and provides global access to it. |
| **Eager Initialization** | Instantiates the singleton object at the start of the application. |
| **Lazy Initialization** | Instantiates the singleton object only when it is first needed. |
| **Thread Safety** | Mechanism to ensure that the singleton is used safely in multi-threaded environments. |
| **Global Access** | The singleton instance can be accessed globally across the application. |

---

## 🔎 Common Interview Questions

- How does the Singleton pattern work, and why is it used?
- What are the pros and cons of using Singleton?
- Can you explain **eager initialization** and **lazy initialization** in Singleton?
- How would you make a Singleton thread-safe in a multi-threaded environment?
- How do you implement the Singleton pattern in Java/Python/Angular?

---

## 🧪 Code Snippets

### ✅ Singleton Pattern - Eager Initialization (Java)
```java
public class Singleton {
    // Create the single instance of the class
    private static final Singleton INSTANCE = new Singleton();

    // Private constructor to prevent instantiation from outside
    private Singleton() {}

    // Public method to access the instance
    public static Singleton getInstance() {
        return INSTANCE;
    }
}
```

### ✅ Singleton Pattern - Lazy Initialization (Java)
```java
public class Singleton {
    private static Singleton instance;

    private Singleton() {}

    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

### ✅ Singleton Pattern - Thread Safe (Java)
```java
public class Singleton {
    private static Singleton instance;

    private Singleton() {}

    public static synchronized Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

### ✅ Singleton in Angular (Using Service)
```typescript
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root',  // Singleton pattern in Angular using providedIn: root
})
export class SingletonService {
  constructor() {}

  getServiceName() {
    return 'SingletonService';
  }
}
```

---

## 🎯 Best Practices Summary

- ✅ **Use Singleton** when you need to ensure that a class has only one instance (e.g., for managing configurations, database connections).
- ✅ **Lazy Initialization** is preferred if the instance is not always needed at the start of the application.
- ✅ **Thread Safety** is a must for Singleton if your application is multi-threaded or runs in a distributed environment.
- ✅ **Singleton** is also commonly used for **logging**, **caching**, or managing **global configuration** settings.

---

## 📘 Cheat Sheet Summary

| Concept | Usage |
|---------|-------|
| Singleton Pattern | Ensures only one instance of a class. |
| Eager Initialization | Instantiates the class at the application start. |
| Lazy Initialization | Instantiates the class only when required. |
| Thread Safety | Ensures the Singleton is safe to use in multi-threaded environments. |

---

## ⚠️ Common Mistakes

| Mistake | Why Avoid |
|---------|-----------|
| Using Singleton unnecessarily | Can lead to global state and increase coupling. |
| Not considering thread safety | Can cause concurrency issues in multi-threaded applications. |
| Using Singleton for everything | Should be used only when necessary; overuse can lead to hard-to-test code. |

---

## 🔗 Extras

- [Design Patterns - Singleton Pattern](https://refactoring.guru/design-patterns/singleton)
- [Java Singleton Implementation](https://www.journaldev.com/1377/java-singleton-design-pattern-best-practices)
- [Angular Dependency Injection](https://angular.io/guide/providers)

---

📌 **Next Recommendation**: Move to `02-Design_Patterns/Factory_Pattern.md` — Learn about creating objects without specifying the exact class of object that will be created.
```
