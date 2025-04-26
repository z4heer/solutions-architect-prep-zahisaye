# 📚 Java Design Patterns Mind Map

Design patterns are proven solutions to common software design problems. They help improve code modularity, reusability, and maintainability. This mind map illustrates key design patterns, categorized by their purpose, with brief definitions and use cases for each.

---

## 🧠 Mind Map

```
Design Patterns
├── Creational Patterns
│   ├── Singleton
│   ├── Factory Method
│   ├── Abstract Factory
│   ├── Builder
│   └── Prototype
├── Structural Patterns
│   ├── Adapter
│   ├── Composite
│   ├── Proxy
│   ├── Decorator
│   └── Facade
└── Behavioral Patterns
    ├── Observer
    ├── Strategy
    ├── Command
    ├── Iterator
    ├── State
    ├── Template Method
    └── Chain of Responsibility
```

---

## 📚 Key Technical Words & Definitions

| Term | Definition |
|------|------------|
| **Singleton** | Ensures that a class has only one instance and provides a global point of access to that instance. |
| **Factory Method** | Defines an interface for creating an object, but lets subclasses alter the type of objects that will be created. |
| **Abstract Factory** | Provides an interface for creating families of related or dependent objects without specifying their concrete classes. |
| **Builder** | Separates the construction of a complex object from its representation, allowing the same construction process to create different representations. |
| **Prototype** | Specifies the kinds of objects to create using a prototypical instance and creates new objects by copying this prototype. |
| **Adapter** | Converts the interface of a class into another interface that a client expects, allowing incompatible interfaces to work together. |
| **Composite** | Composes objects into tree structures to represent part-whole hierarchies, allowing clients to treat individual objects and composites uniformly. |
| **Proxy** | Provides an object representing another object, controlling access to it. This can be used for lazy loading, security, etc. |
| **Decorator** | Adds additional functionality to an object dynamically, without altering its structure. |
| **Facade** | Provides a simplified interface to a complex subsystem, making it easier to use. |
| **Observer** | Defines a one-to-many dependency between objects, where a change in one object triggers updates in all its dependents. |
| **Strategy** | Defines a family of algorithms, encapsulates each one, and makes them interchangeable, allowing the algorithm to be selected at runtime. |
| **Command** | Encapsulates a request as an object, allowing users to parameterize clients with queues, requests, and operations. |
| **Iterator** | Provides a way to access the elements of an aggregate object sequentially without exposing its underlying representation. |
| **State** | Allows an object to alter its behavior when its internal state changes, appearing as if the object changed its class. |
| **Template Method** | Defines the structure of an algorithm, allowing certain steps to be overridden by subclasses without changing the algorithm's structure. |
| **Chain of Responsibility** | Allows passing a request along a chain of handlers, where each handler processes the request or passes it along the chain. |

---

## 🔎 Common Interview Questions

- What are the differences between the Factory Method and Abstract Factory patterns?
- How does the Singleton pattern ensure that only one instance of a class is created, and what are its use cases?
- Can you explain the purpose of the Builder pattern and how it improves the construction of complex objects?
- What is the difference between the Proxy and Decorator patterns? When would you use each of them?
- How does the Observer pattern facilitate communication between objects in a decoupled way?
- What are the key benefits of using the Strategy pattern in place of conditionals for algorithm selection?

---

## 🧪 Code Snippets

### Example: Singleton Pattern

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

### Example: Factory Method Pattern

```java
abstract class Product {
    public abstract void use();
}

class ConcreteProductA extends Product {
    public void use() {
        System.out.println("Using Product A");
    }
}

class ConcreteProductB extends Product {
    public void use() {
        System.out.println("Using Product B");
    }
}

abstract class Creator {
    public abstract Product factoryMethod();
}

class ConcreteCreatorA extends Creator {
    public Product factoryMethod() {
        return new ConcreteProductA();
    }
}

class ConcreteCreatorB extends Creator {
    public Product factoryMethod() {
        return new ConcreteProductB();
    }
}
```

### Example: Observer Pattern

```java
import java.util.ArrayList;
import java.util.List;

interface Observer {
    void update(String message);
}

class ConcreteObserver implements Observer {
    private String name;

    public ConcreteObserver(String name) {
        this.name = name;
    }

    @Override
    public void update(String message) {
        System.out.println(name + " received: " + message);
    }
}

class Subject {
    private List<Observer> observers = new ArrayList<>();

    public void addObserver(Observer observer) {
        observers.add(observer);
    }

    public void removeObserver(Observer observer) {
        observers.remove(observer);
    }

    public void notifyObservers(String message) {
        for (Observer observer : observers) {
            observer.update(message);
        }
    }
}

public class ObserverExample {
    public static void main(String[] args) {
        Subject subject = new Subject();
        Observer observer1 = new ConcreteObserver("Observer 1");
        Observer observer2 = new ConcreteObserver("Observer 2");

        subject.addObserver(observer1);
        subject.addObserver(observer2);

        subject.notifyObservers("Hello Observers!");
    }
}
```

---

## 🎯 Best Practices Summary

- ✅ Use the **Singleton pattern** for managing shared resources like database connections.
- ✅ Choose **Factory Method** or **Abstract Factory** when creating related objects without specifying their concrete class.
- ✅ The **Builder pattern** helps in constructing complex objects, especially when they have many optional parameters.
- ✅ Use **Decorator** for adding functionality dynamically to objects without changing their code.
- ✅ Implement **Observer** when there is a need for one-to-many dependency, such as event-driven systems.
- ✅ Avoid creating unnecessary subclasses by using **Strategy** to switch algorithms at runtime.

---

## 📘 Cheat Sheet Summary

| Concept | Usage |
|---------|-------|
| **Singleton** | Ensures a single instance of a class, used for resources like logging or configuration. |
| **Factory Method** | Use when the exact class to instantiate is not known in advance. |
| **Observer** | Use when one object needs to notify others about changes without tightly coupling them. |
| **Decorator** | Use when you need to add functionality to an object without altering its structure. |
| **Facade** | Use to simplify complex systems by providing a unified interface. |

---

## ⚠️ Common Mistakes

| Mistake | Why Avoid |
|---------|-----------|
| Not considering thread-safety for Singleton | Can lead to race conditions in multi-threaded environments. |
| Using the wrong design pattern for a problem | Leads to overcomplication or misuse of resources. |
| Not understanding when to use certain patterns like **Strategy** over simple conditionals | Reduces code clarity and increases maintenance difficulty. |

---

## 🔗 Extras

- [Design Patterns Documentation](https://refactoring.guru/design-patterns)
- [GoF Design Patterns](https://www.oreilly.com/library/view/design-patterns-elements/0201633612/)
