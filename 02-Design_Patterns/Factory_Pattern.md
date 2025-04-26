# 📚 Factory Pattern

The **Factory Pattern** is a **creational design pattern** that provides an interface for creating objects, but allows subclasses or client code to alter the type of objects that will be created. It decouples object creation from the client, making the system more flexible and scalable.

---

## 🧠 Mind Map

```
Factory Pattern
├── Definition
├── When to Use
├── Types
│   ├── Simple Factory
│   ├── Factory Method
│   └── Abstract Factory
├── Advantages
├── Disadvantages
├── Implementation
│   ├── Simple Factory Example
│   ├── Factory Method Example
│   └── Abstract Factory Example
```

---

## 📚 Key Technical Words & Definitions

| Term | Definition |
|------|------------|
| **Factory Pattern** | A design pattern used to create objects without specifying the exact class of object that will be created. |
| **Simple Factory** | A factory method that returns different types of objects based on the input parameter. |
| **Factory Method** | A method in a class that returns an instance of a class, but lets subclasses decide which class to instantiate. |
| **Abstract Factory** | A pattern for creating families of related or dependent objects without specifying their concrete classes. |
| **Object Creation** | The process of instantiating new objects in the system, which is handled by the factory in the Factory Pattern. |

---

## 🔎 Common Interview Questions

- What is the Factory Pattern, and how does it work?
- What is the difference between **Simple Factory**, **Factory Method**, and **Abstract Factory**?
- How does the Factory Pattern promote **loose coupling** in an application?
- Can you explain how **Factory Method** differs from **Abstract Factory** in object creation?
- How do you implement the Factory Pattern in Java/Python/Angular?

---

## 🧪 Code Snippets

### ✅ Simple Factory (Java)
```java
class Animal {
    public void speak() {
        System.out.println("Animal speaks");
    }
}

class Dog extends Animal {
    @Override
    public void speak() {
        System.out.println("Woof");
    }
}

class Cat extends Animal {
    @Override
    public void speak() {
        System.out.println("Meow");
    }
}

class AnimalFactory {
    public static Animal getAnimal(String type) {
        if (type.equals("dog")) {
            return new Dog();
        } else if (type.equals("cat")) {
            return new Cat();
        }
        return null;
    }
}
```

### ✅ Factory Method (Java)
```java
abstract class Animal {
    public abstract void speak();
}

class Dog extends Animal {
    @Override
    public void speak() {
        System.out.println("Woof");
    }
}

class Cat extends Animal {
    @Override
    public void speak() {
        System.out.println("Meow");
    }
}

abstract class AnimalFactory {
    public abstract Animal createAnimal();
}

class DogFactory extends AnimalFactory {
    @Override
    public Animal createAnimal() {
        return new Dog();
    }
}

class CatFactory extends AnimalFactory {
    @Override
    public Animal createAnimal() {
        return new Cat();
    }
}
```

### ✅ Abstract Factory (Java)
```java
interface Animal {
    void speak();
}

class Dog implements Animal {
    @Override
    public void speak() {
        System.out.println("Woof");
    }
}

class Cat implements Animal {
    @Override
    public void speak() {
        System.out.println("Meow");
    }
}

interface AnimalFactory {
    Animal createAnimal();
}

class DogFactory implements AnimalFactory {
    @Override
    public Animal createAnimal() {
        return new Dog();
    }
}

class CatFactory implements AnimalFactory {
    @Override
    public Animal createAnimal() {
        return new Cat();
    }
}
```

---

## 🎯 Best Practices Summary

- ✅ Use **Factory Pattern** when the exact type of object to be created cannot be determined until runtime.
- ✅ **Factory Method** is useful when you want to delegate object creation to subclasses.
- ✅ **Abstract Factory** is a better choice when you need to create families of related objects.
- ✅ Keep the object creation process in a **separate factory class** to promote **separation of concerns**.
- ✅ The **Factory Pattern** is useful for decoupling the client code from the instantiation logic, making it more flexible to change the underlying objects without affecting the client.

---

## 📘 Cheat Sheet Summary

| Concept | Usage |
|---------|-------|
| Factory Pattern | A creational pattern that abstracts the object creation process. |
| Simple Factory | A factory method that returns an object based on input. |
| Factory Method | A method in a class that delegates object creation to subclasses. |
| Abstract Factory | Creates families of related objects without specifying their concrete classes. |

---

## ⚠️ Common Mistakes

| Mistake | Why Avoid |
|---------|-----------|
| Using **Simple Factory** when the object creation logic is complex | It can lead to large factory classes and decrease flexibility. |
| Overusing the **Factory Pattern** | Use only when object creation logic needs to be abstracted. |
| Forgetting to add **error handling** for invalid inputs | Can lead to runtime errors if an invalid object type is requested. |

---

## 🔗 Extras

- [Design Patterns - Factory Method](https://refactoring.guru/design-patterns/factory-method)
- [Factory Pattern Explained](https://sourcemaking.com/design_patterns/factory_method)
- [Abstract Factory Pattern](https://refactoring.guru/design-patterns/abstract-factory)
