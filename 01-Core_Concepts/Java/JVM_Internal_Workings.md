# 📚 JVM Internal Workings

Understanding how JVM works internally is crucial for system design, performance optimization, and troubleshooting at Solutions Architect level.

---

## 🧠 Mind Map

```
JVM Architecture
├── Class Loader Subsystem
│   ├── Loading
│   ├── Linking
│   └── Initialization
├── Runtime Data Areas
│   ├── Method Area
│   ├── Heap
│   ├── Stack
│   ├── PC Register
│   └── Native Method Stack
├── Execution Engine
│   ├── Interpreter
│   ├── JIT Compiler
│   └── Garbage Collector
├── Native Interface
│   └── JNI (Java Native Interface)
├── Native Method Libraries
```

---

## 📚 Key Technical Words & Definitions

| Term | Definition |
|------|------------|
| **ClassLoader** | Loads `.class` files into JVM memory. |
| **Method Area** | Stores class structure (methods, fields, constants). |
| **Heap** | Runtime storage for all objects and instance variables. |
| **Stack** | Per-thread memory for method call frames (local variables, operands). |
| **Program Counter (PC) Register** | Points to the current executing instruction. |
| **Native Method Stack** | Supports native methods (e.g., C/C++). |
| **Execution Engine** | Executes the bytecode instructions. |
| **Interpreter** | Reads bytecode instructions one by one. |
| **JIT Compiler** | Converts bytecode to native machine code at runtime for better performance. |
| **Garbage Collector (GC)** | Automatically reclaims unused memory. |

---

## 🔎 Common Interview Questions

- What happens from `.java` to execution in JVM?
- Explain JVM Memory Areas.
- Difference between Heap and Stack in JVM?
- How does Garbage Collection work?
- Role of JIT Compiler?
- How to monitor JVM performance?

---

## 🧪 Code Snippets & Diagrams

### ✅ Simple Memory Leak Example
```java
import java.util.ArrayList;
import java.util.List;

public class MemoryLeakDemo {
    public static void main(String[] args) {
        List<int[]> leakyList = new ArrayList<>();
        while (true) {
            leakyList.add(new int[100000]);
        }
    }
}
```
_(This will cause OutOfMemoryError after heap fills up.)_

---

## ⚠️ JVM Memory Areas Explained

| Area | Details |
|------|---------|
| Method Area | Class-level data shared among threads. |
| Heap | Objects and arrays live here (shared across threads). |
| Stack | Each thread has its own stack, contains frames for each method call. |
| PC Register | Each thread has one, points to next instruction. |
| Native Method Stack | For native language integration (C/C++ methods). |

---

## 🎯 Best Practices Summary

- ✅ Always release references to large objects when no longer needed.
- ✅ Monitor Garbage Collection (GC) using tools like `jstat`, `VisualVM`.
- ✅ Tune JVM options for production (`-Xms`, `-Xmx`, `-XX:+UseG1GC`).
- ✅ Avoid unnecessary object creation (favor object pooling when appropriate).
- ✅ Understand GC types: Serial, Parallel, CMS, G1 GC.

---

## 📘 Cheat Sheet Summary

| Topic | Summary |
|-------|---------|
| JVM Loading | Bootstrap > Extension > Application ClassLoaders. |
| Bytecode Execution | Interpreter first → JIT-compiled hot code paths. |
| GC | Minor GC (Young Gen) vs Major GC (Old Gen). |
| Memory Errors | `OutOfMemoryError`, `StackOverflowError`. |
| JIT Optimization | Method inlining, loop unrolling, escape analysis. |

---

## 🔗 Extras

- [Oracle JVM Internals Documentation](https://docs.oracle.com/javase/specs/jvms/se8/html/)
- [Memory Management in Java (Baeldung)](https://www.baeldung.com/java-memory-management)

---
