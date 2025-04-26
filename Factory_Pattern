# 📚 Factory Pattern

The **Factory Pattern** is a **creational design pattern** used to create objects without specifying the exact class of object that will be created.

---

## 🧠 Mind Map

```
Factory Pattern
├── Definition
├── When to Use
├── Participants
│   ├── Creator
│   ├── ConcreteCreator
│   └── Product
├── Types of Factory Patterns
│   ├── Simple Factory
│   ├── Factory Method
│   └── Abstract Factory
├── Advantages
├── Disadvantages
├── Implementation
```

---

## 📚 Key Technical Words & Definitions

| Term | Definition |
|------|------------|
| **Factory Pattern** | Provides an interface for creating objects, but allows subclasses to alter the type of objects that will be created. |
| **Creator** | Declares the factory method. |
| **ConcreteCreator** | Implements the factory method to create objects. |
| **Product** | The object being created by the factory method. |

---

## 🔎 Common Interview Questions

- What is the Factory Pattern and how does it work?
- How is Factory Pattern different from Singleton and Builder?
- What is the difference between Factory Method and Abstract Factory?
- When would you use a Factory Method over a Constructor?
- Can you show an example of using the Factory Method in Java?

---

## 🧪 Code Snippets

### Simple Factory Example (Java)
```java
// Product
public interface Animal {
    void sound();
}

// Concrete Product
class Dog implements Animal {
    public void sound() {
        System.out.println("Bark");
    }
}

class Cat implements Animal {
    public void sound() {
        System.out.println("Meow");
    }
}

// Creator
public class AnimalFactory {
    public static Animal getAnimal(String type) {
        if (type.equals("Dog")) {
            return new Dog();
        } else if (type.equals("Cat")) {
            return new Cat();
        }
        return null;
    }
}

// Usage
public class Main {
    public static void main(String[] args) {
        Animal dog = AnimalFactory.getAnimal("Dog");
        dog.sound();
    }
}
```

### Factory Method Example (Java)
```java
// Product
interface Animal {
    void sound();
}

// Concrete Product
class Dog implements Animal {
    public void sound() {
        System.out.println("Bark");
    }
}

// Creator
abstract class AnimalCreator {
    public abstract Animal createAnimal();

    public void makeSound() {
        Animal animal = createAnimal();
        animal.sound();
    }
}

// Concrete Creator
class DogCreator extends AnimalCreator {
    public Animal createAnimal() {
        return new Dog();
    }
}

// Usage
public class Main {
    public static void main(String[] args) {
        AnimalCreator creator = new DogCreator();
        creator.makeSound();
    }
}
```

---

## 🎯 Best Practices Summary

- ✅ Use Factory Pattern when the exact class of the object is not known until runtime.
- ✅ Use Factory Method when you need to create objects dynamically.
- ✅ Factory helps to **decouple** object creation and client code.

---

## 📘 Cheat Sheet Summary

| Concept | Usage |
|---------|-------|
| Factory Pattern | Create objects without exposing the creation logic. |
| Factory Method | Provides a method for creating an object. |
| Abstract Factory | Creates families of related objects. |

---

## ⚠️ Common Mistakes

| Mistake | Why Avoid |
|---------|-----------|
| Using Factory when not needed | Increases complexity unnecessarily. |
| Returning null or throwing exceptions | May lead to hidden bugs. |
| Not decoupling class dependencies properly | Violates the open/closed principle. |

---

## 🔗 Extras

- [Factory Design Pattern - Refactoring Guru](https://refactoring.guru/design-patterns/factory-method)
- [Factory Pattern Implementation](https://www.baeldung.com/java/factory-pattern)
