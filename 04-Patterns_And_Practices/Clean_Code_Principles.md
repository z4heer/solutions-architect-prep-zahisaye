# Clean Code Principles

Key principles and practices to write clean, maintainable, and scalable code.

---

## 🧠 Mind Map

- **SOLID Principles**
- **DRY (Don't Repeat Yourself)**
- **KISS (Keep It Simple, Stupid)**
- **YAGNI (You Aren't Gonna Need It)**
- **Boy Scout Rule**
- **Single Responsibility Principle**
- **Code Readability and Naming**

---

## 🎯 Key Technical Words & Definitions

| Principle | Definition |
|:----------|:------------|
| SOLID | Five design principles for object-oriented programming to achieve better maintainability. |
| DRY | Avoid code duplication by abstracting repeated logic. |
| KISS | Simplicity leads to better maintainability and fewer bugs. |
| YAGNI | Only implement functionality when necessary. |
| Boy Scout Rule | Always leave the code better than you found it. |
| Single Responsibility Principle | A class should have only one reason to change. |

---

## ❓ Common Interview Questions

- What is the Single Responsibility Principle and why is it important?
- Explain the DRY principle with an example.
- Why is simplicity important in software design?
- How do you apply SOLID principles in real projects?
- What does “Clean Code” mean to you?

---

## 🛠️ Code Snippet Example - Applying Single Responsibility

```java
public class Invoice {
    private double amount;

    public double calculateTotal() {
        // logic to calculate invoice total
    }
}

public class InvoicePrinter {
    public void print(Invoice invoice) {
        // logic to print invoice
    }
}
```
*Instead of one class doing both calculation and printing, separate concerns into different classes.*

---

## ✅ Best Practices Summary

- Write self-explanatory, expressive code (code should explain itself).
- Functions should be small and do one thing.
- Classes should have a single responsibility.
- Favor meaningful names over comments explaining bad code.
- Continuously refactor for better design.
- Prioritize readability over cleverness.

---

## 🚫 Common Mistakes

- Overcomplicating simple logic (violating KISS).
- Duplicating code across modules (violating DRY).
- Large classes or methods doing too many things.
- Writing code for hypothetical future requirements (violating YAGNI).

---

## 📋 Cheat Sheet Summary

| Principle | Reminder |
|:----------|:---------|
| SRP | One reason to change |
| OCP | Open for extension, closed for modification |
| LSP | Subtypes should be substitutable for base types |
| ISP | Prefer many small interfaces |
| DIP | Depend on abstractions, not concretions |
| DRY | No duplication |
| KISS | Keep it simple |
| YAGNI | Don't code it until it's needed |

---

✅  
Shall I continue with **04-Patterns_And_Practices/Microservices_Best_Practices.md**? 🚀
