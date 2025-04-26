# 📚 Java Collections Deep Dive

A foundational concept every Solutions Architect must master — not just to write code, but to design robust systems with the right data structures.

---

## 🧠 Mind Map

```
Collections Framework
├── Interfaces
│   ├── List → ArrayList, LinkedList, Vector, Stack
│   ├── Set → HashSet, LinkedHashSet, TreeSet
│   └── Map → HashMap, LinkedHashMap, TreeMap, Hashtable
├── Queue → PriorityQueue, ArrayDeque
└── Utilities → Collections, Arrays, EnumSet, EnumMap
```

---

## 📚 Key Technical Words & Definitions

| Term | Definition |
|------|------------|
| **List** | Ordered collection (allows duplicates). |
| **Set** | Unordered collection (no duplicates). |
| **Map** | Key-value pair collection. Keys must be unique. |
| **ArrayList** | Resizable array; random access is fast, slow insertions/deletions. |
| **LinkedList** | Doubly-linked list; fast insert/delete, slow random access. |
| **HashSet** | Hash-based Set, no duplicates, no order. |
| **TreeSet** | Sorted Set using Red-Black tree. |
| **HashMap** | Hash table based Map, allows one null key. |
| **TreeMap** | Sorted map based on natural/comparator order. |
| **ConcurrentHashMap** | Thread-safe, lock-striping based Map. |
| **EnumSet/EnumMap** | High-performance Set/Map for enums. |
| **Collections.unmodifiableList** | Read-only wrapper over a List. |

---

## 🔎 Common Interview Questions

- When would you use `LinkedHashMap` over `HashMap`?
- How does `HashMap` handle collisions?
- Why `ConcurrentHashMap` over `Hashtable`?
- Can a `HashSet` contain null?
- How does `TreeMap` maintain order?

---

## 🧪 Code Snippets

### ✅ Using a HashMap
```java
Map<String, Integer> stock = new HashMap<>();
stock.put("RELIANCE", 10);
stock.put("TCS", 5);
System.out.println(stock.get("TCS")); // 5
```

### ✅ TreeSet with Comparator
```java
Set<String> names = new TreeSet<>(Comparator.reverseOrder());
names.add("Apple");
names.add("Google");
System.out.println(names); // [Google, Apple]
```

### ✅ ConcurrentHashMap for Thread Safety
```java
Map<String, Integer> map = new ConcurrentHashMap<>();
map.put("Threads", 100);
```

---

## ⚠️ Tricky Edge Cases

| Scenario | Notes |
|----------|-------|
| `HashMap` with null key | Allowed only one null key. |
| `TreeMap` with null key | Throws `NullPointerException`. |
| Iterating over `ConcurrentHashMap` | Weakly consistent, doesn’t throw `ConcurrentModificationException`. |
| `LinkedHashMap` access order | Can be used for **LRU cache** if `accessOrder=true`. |

---

## 🎯 Use in Real Projects

| Use Case | Collection |
|----------|------------|
| LRU Cache | `LinkedHashMap` with accessOrder |
| Thread-safe API cache | `ConcurrentHashMap` |
| Sorted dropdown options | `TreeSet` |
| Enum config mapping | `EnumMap` |

---

## 📘 Cheat Sheet Summary

- Use `ArrayList` for fast reads, `LinkedList` for frequent inserts.
- Use `HashSet` to eliminate duplicates fast.
- Use `LinkedHashMap` for predictable iteration.
- Use `ConcurrentHashMap` for high-concurrency maps.
- Never use `Hashtable` in modern code.

---

## 🔗 Extras

- [Java Collections Javadoc](https://docs.oracle.com/javase/8/docs/technotes/guides/collections/overview.html)
- [Java Collections Cheat Sheet PDF (external)](https://cheatography.com/hans/cheat-sheets/java-collections/)

---

📌 **Next Recommendation**: Read `Multithreading_Best_Practices.md` and implement an LRU Cache using `LinkedHashMap` in `/03-Projects/JavaSnippets/LRUCache.java`.

```
