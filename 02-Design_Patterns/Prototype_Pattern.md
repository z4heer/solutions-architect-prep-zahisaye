# 📚 Prototype Pattern

The **Prototype Pattern** is a **creational design pattern** that allows you to copy existing objects without making the code dependent on their concrete classes. Instead of creating new instances, it clones existing ones, improving performance and flexibility.

---

## 🧠 Mind Map

```
Prototype Pattern
├── Definition
├── When to Use
├── Participants
│   ├── Prototype Interface
│   ├── Concrete Prototype
├── Shallow vs Deep Copy
├── Advantages
├── Disadvantages
├── Implementation
```

---

## 📚 Key Technical Words & Definitions

| Term | Definition |
|------|------------|
| **Prototype Pattern** | Cloning existing objects to create new ones without depending on their classes. |
| **Prototype Interface** | Declares a method for cloning itself. |
| **Concrete Prototype** | Implements the clone operation. |
| **Shallow Copy** | Copies only field values, without copying referenced objects deeply. |
| **Deep Copy** | Recursively copies referenced objects, making a fully independent clone. |

---

## 🔎 Common Interview Questions

- What is the Prototype Pattern, and where is it used?
- What is the difference between **shallow copy** and **deep copy**?
- Why and when would you prefer using the Prototype Pattern over other creation patterns?
- How is cloning implemented in Java (Cloneable interface)?
- Can you give examples of real-world systems using the Prototype Pattern?

---

## 🧪 Code Snippets

### ✅ Basic Prototype (Java)
```java
// Prototype Interface
public interface Prototype {
    Prototype clone();
}

// Concrete Prototype
public class Car implements Prototype {
    private String model;
    private int wheels;

    public Car(String model, int wheels) {
        this.model = model;
        this.wheels = wheels;
    }

    @Override
    public Prototype clone() {
        return new Car(model, wheels);
    }

    @Override
    public String toString() {
        return "Car [Model=" + model + ", Wheels=" + wheels + "]";
    }
}

// Usage
public class Main {
    public static void main(String[] args) {
        Car original = new Car("Tesla Model S", 4);
        Car copy = (Car) original.clone();

        System.out.println(original);
        System.out.println(copy);
    }
}
```

---

### ✅ Using Java's Cloneable Interface
```java
public class Car implements Cloneable {
    private String model;
    private int wheels;

    public Car(String model, int wheels) {
        this.model = model;
        this.wheels = wheels;
    }

    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone(); // shallow copy
    }

    @Override
    public String toString() {
        return "Car [Model=" + model + ", Wheels=" + wheels + "]";
    }
}

public class Main {
    public static void main(String[] args) throws CloneNotSupportedException {
        Car car1 = new Car("BMW X5", 4);
        Car car2 = (Car) car1.clone();

        System.out.println(car1);
        System.out.println(car2);
    }
}
```

---

## 🛠️ Shallow Copy vs Deep Copy (Quick Comparison)

| Aspect | Shallow Copy | Deep Copy |
|--------|--------------|-----------|
| References | Copied as-is (same object) | New instances created |
| Performance | Faster | Slower |
| Use Case | Lightweight objects | Complex object graphs |

---

## 🎯 Best Practices Summary

- ✅ Use Prototype Pattern for object creation when instantiation is expensive.
- ✅ Implement **deep copy** if the object contains nested objects.
- ✅ Avoid cloning immutable objects (better to reuse them directly).
- ✅ Handle **CloneNotSupportedException** properly in Java.

---

## 📘 Cheat Sheet Summary

| Concept | Usage |
|---------|-------|
| Prototype Pattern | To create a copy of an existing object without knowing its class. |
| Shallow Copy | Copies values but shared object references. |
| Deep Copy | Copies both values and referenced objects. |
| Cloneable Interface | Java’s built-in way to support object cloning. |

---

## ⚠️ Common Mistakes

| Mistake | Why Avoid |
|---------|-----------|
| Not properly handling deep copies when needed | Causes bugs due to shared references. |
| Cloning mutable objects without precautions | Leads to side effects and data corruption. |
| Forgetting to override `clone()` properly | Default `Object.clone()` may not behave as expected. |

---

## 🔗 Extras

- [Prototype Pattern - Refactoring Guru](https://refactoring.guru/design-patterns/prototype)
- [Deep Copy vs Shallow Copy in Java](https://www.baeldung.com/java-deep-copy)
- [Cloneable Interface Explained](https://www.geeksforgeeks.org/cloneable-interface-in-java/)
