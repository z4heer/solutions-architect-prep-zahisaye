# 📚 Builder Pattern

The **Builder Pattern** is a **creational design pattern** that allows you to create complex objects step-by-step. It separates the construction of a complex object from its representation, allowing the same construction process to create different representations.

---

## 🧠 Mind Map

```
Builder Pattern
├── Definition
├── When to Use
├── Participants
│   ├── Builder
│   ├── ConcreteBuilder
│   ├── Director
│   └── Product
├── Advantages
├── Disadvantages
├── Implementation
```

---

## 📚 Key Technical Words & Definitions

| Term | Definition |
|------|------------|
| **Builder Pattern** | Constructs complex objects step-by-step, isolating the construction code from the object's representation. |
| **Builder** | Abstract interface for creating parts of a Product object. |
| **ConcreteBuilder** | Provides specific implementations for the construction process. |
| **Director** | Defines the order and process for building a complex object using a Builder. |
| **Product** | The complex object that is being built. |

---

## 🔎 Common Interview Questions

- What is the Builder Pattern, and how does it work?
- How is the Builder Pattern different from the Factory Pattern?
- When should you use the Builder Pattern?
- How do you implement the Builder Pattern in Java/Python?
- What are the advantages of using the Builder Pattern in large object creation?

---

## 🧪 Code Snippets

### ✅ Classic Builder Pattern (Java)
```java
// Product
public class Car {
    private String engine;
    private int wheels;
    private boolean sunroof;

    public void setEngine(String engine) {
        this.engine = engine;
    }

    public void setWheels(int wheels) {
        this.wheels = wheels;
    }

    public void setSunroof(boolean sunroof) {
        this.sunroof = sunroof;
    }

    @Override
    public String toString() {
        return "Car [Engine=" + engine + ", Wheels=" + wheels + ", Sunroof=" + sunroof + "]";
    }
}

// Builder
interface CarBuilder {
    void buildEngine();
    void buildWheels();
    void buildSunroof();
    Car getCar();
}

// ConcreteBuilder
class SportsCarBuilder implements CarBuilder {
    private Car car = new Car();

    public void buildEngine() {
        car.setEngine("V8 Engine");
    }

    public void buildWheels() {
        car.setWheels(4);
    }

    public void buildSunroof() {
        car.setSunroof(true);
    }

    public Car getCar() {
        return car;
    }
}

// Director
class Director {
    public Car construct(CarBuilder builder) {
        builder.buildEngine();
        builder.buildWheels();
        builder.buildSunroof();
        return builder.getCar();
    }
}
```

### ✅ Fluent Builder Pattern (Modern Java)
```java
public class Car {
    private String engine;
    private int wheels;
    private boolean sunroof;

    private Car(Builder builder) {
        this.engine = builder.engine;
        this.wheels = builder.wheels;
        this.sunroof = builder.sunroof;
    }

    public static class Builder {
        private String engine;
        private int wheels;
        private boolean sunroof;

        public Builder engine(String engine) {
            this.engine = engine;
            return this;
        }

        public Builder wheels(int wheels) {
            this.wheels = wheels;
            return this;
        }

        public Builder sunroof(boolean sunroof) {
            this.sunroof = sunroof;
            return this;
        }

        public Car build() {
            return new Car(this);
        }
    }

    @Override
    public String toString() {
        return "Car [Engine=" + engine + ", Wheels=" + wheels + ", Sunroof=" + sunroof + "]";
    }
}
```

### ✅ Usage
```java
Car car = new Car.Builder()
               .engine("V6 Engine")
               .wheels(4)
               .sunroof(true)
               .build();
System.out.println(car);
```

---

## 🎯 Best Practices Summary

- ✅ Use Builder Pattern for constructing **complex objects** with many optional attributes.
- ✅ Separate **construction logic** from the final object representation.
- ✅ Prefer **Fluent Builders** for modern Java (better readability and immutability).
- ✅ **Director** is optional if client code itself controls the building steps.

---

## 📘 Cheat Sheet Summary

| Concept | Usage |
|---------|-------|
| Builder Pattern | Step-by-step object construction and separation of concerns. |
| Classic Builder | Interface + Concrete Builder + Director + Product. |
| Fluent Builder | Modern, readable approach using inner static classes. |
| Complex Object | Useful when multiple configurations are needed for the same object. |

---

## ⚠️ Common Mistakes

| Mistake | Why Avoid |
|---------|-----------|
| Not using a builder when many parameters are optional | Leads to telescoping constructors. |
| Exposing internal object creation details | Breaks encapsulation. |
| Forgetting to make the Builder class **static** | Can cause unexpected memory leaks. |

---

## 🔗 Extras

- [Design Patterns - Builder Pattern](https://refactoring.guru/design-patterns/builder)
- [Effective Java - Builder Pattern](https://amzn.to/3XYq5hd)
- [Fluent Builders Explained](https://www.baeldung.com/java-builder-pattern)

---

📌 **Next Recommendation**: Move to `02-Design_Patterns/Prototype_Pattern.md` — Learn about cloning objects for fast object creation!

```
