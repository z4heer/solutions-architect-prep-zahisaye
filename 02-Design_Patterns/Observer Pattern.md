# 📚 Observer Pattern

The **Observer Pattern** is a **behavioral design pattern** where an object (the "subject") maintains a list of its dependent observers, and notifies them automatically of any changes to its state.

---

## 🧠 Mind Map

```
Observer Pattern
├── Definition
├── When to Use
├── Participants
│   ├── Subject
│   ├── Observer
│   ├── ConcreteSubject
│   └── ConcreteObserver
├── Advantages
├── Disadvantages
├── Implementation
```

---

## 📚 Key Technical Words & Definitions

| Term | Definition |
|------|------------|
| **Observer Pattern** | A behavioral pattern where a subject notifies observers about state changes. |
| **Subject** | The object being observed, which holds a list of observers. |
| **Observer** | The interface that gets updated when the subject’s state changes. |
| **ConcreteObserver** | The actual observer implementation. |
| **ConcreteSubject** | The concrete implementation of the subject. |

---

## 🔎 Common Interview Questions

- What is the Observer Pattern, and where would you use it?
- How is Observer Pattern implemented in Java?
- Can you explain the **push** and **pull** methods in the Observer Pattern?
- How does the Observer Pattern differ from the Mediator Pattern?
- What are the drawbacks of using the Observer Pattern?

---

## 🧪 Code Snippets

### Basic Observer Pattern (Java)
```java
// Observer
interface Observer {
    void update(String message);
}

// ConcreteObserver
class ConcreteObserver implements Observer {
    private String name;

    public ConcreteObserver(String name) {
        this.name = name;
    }

    public void update(String message) {
        System.out.println(name + " received message: " + message);
    }
}

// Subject
interface Subject {
    void addObserver(Observer observer);
    void removeObserver(Observer observer);
    void notifyObservers(String message);
}

// ConcreteSubject
class ConcreteSubject implements Subject {
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

// Usage
public class Main {
    public static void main(String[] args) {
        ConcreteSubject subject = new ConcreteSubject();

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

- ✅ Use the Observer Pattern when one object needs to notify multiple objects about state changes.
- ✅ Ensure observers are decoupled from the subject to avoid tight coupling.
- ✅ Use the pattern when there are multiple event listeners or updates from various sources.

---

## 📘 Cheat Sheet Summary

| Concept | Usage |
|---------|-------|
| Observer Pattern | Subject notifies dependent observers of state changes. |
| Push vs Pull | Push: Notify with data; Pull: Observer pulls data when needed. |
| Loose Coupling | Observers and subjects should be decoupled. |

---

## ⚠️ Common Mistakes

| Mistake | Why Avoid |
|---------|-----------|
| Not managing observers properly | Leads to memory leaks (observers not removed). |
| Tight coupling between subject and observer | Breaks flexibility and testability. |
| Not limiting the number of observers | Can cause performance issues. |

---

## 🔗 Extras

- [Observer Design Pattern - Refactoring Guru](https://refactoring.guru/design-patterns/observer)
- [Java Observer Pattern](https://www.baeldung.com/java/observer-pattern)
