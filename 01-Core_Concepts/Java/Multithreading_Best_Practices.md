# 📚 Java Multithreading Best Practices

Multithreading is critical for building scalable, responsive, and efficient applications — a key skill for Solutions Architects.

---

## 🧠 Mind Map

```
Multithreading
├── Core Concepts
│   ├── Thread Creation
│   ├── Thread Lifecycle
│   └── Thread Synchronization
├── Concurrency Utilities
│   ├── ExecutorService
│   ├── Future, Callable
│   ├── CountDownLatch
│   ├── Semaphore
│   ├── ReentrantLock
│   └── ForkJoinPool
├── Best Practices
│   ├── Use Executor frameworks
│   ├── Avoid Thread.sleep
│   ├── Minimize synchronization
│   ├── Prefer immutability
│   └── Use concurrent collections
```

---

## 📚 Key Technical Words & Definitions

| Term | Definition |
|------|------------|
| **Thread** | Lightweight process for concurrent execution. |
| **Runnable** | Functional interface for defining a thread task. |
| **Callable** | Like Runnable but can return a value and throw exceptions. |
| **ExecutorService** | Framework for managing a pool of threads. |
| **Future** | Represents the result of an asynchronous computation. |
| **Synchronized** | Keyword to control access to critical sections. |
| **Lock** | Explicit locking (more flexible than `synchronized`). |
| **CountDownLatch** | Synchronizer to block until other threads complete. |
| **Semaphore** | Controls access to a resource by multiple threads. |
| **ForkJoinPool** | Optimized thread pool for divide-and-conquer tasks. |

---

## 🔎 Common Interview Questions

- Difference between `Runnable` and `Callable`?
- Why prefer `ExecutorService` over manually creating threads?
- How to prevent deadlocks?
- What is thread starvation?
- Explain thread safety vs immutability.

---

## 🧪 Code Snippets

### ✅ Creating a Thread Using ExecutorService
```java
ExecutorService executor = Executors.newFixedThreadPool(2);
executor.submit(() -> {
    System.out.println("Thread running: " + Thread.currentThread().getName());
});
executor.shutdown();
```

### ✅ Using Callable and Future
```java
ExecutorService executor = Executors.newSingleThreadExecutor();
Future<Integer> future = executor.submit(() -> 2 + 3);
System.out.println(future.get()); // Output: 5
executor.shutdown();
```

### ✅ Using CountDownLatch
```java
CountDownLatch latch = new CountDownLatch(3);

for (int i = 0; i < 3; i++) {
    new Thread(() -> {
        System.out.println("Thread completed");
        latch.countDown();
    }).start();
}

latch.await(); // Main thread waits here
System.out.println("All threads completed.");
```

---

## ⚠️ Tricky Edge Cases

| Scenario | Notes |
|----------|-------|
| Deadlock | Two threads hold locks waiting for each other → Always acquire locks in the same order. |
| Thread Pool Exhaustion | Not shutting down ExecutorService can lead to memory leaks. |
| Race Condition | Always access shared mutable data carefully (synchronized or concurrent structures). |
| Busy Waiting | Avoid constant polling (`Thread.sleep`); prefer wait/notify. |

---

## 🎯 Best Practices Summary

- ✅ Always prefer **ExecutorService** over manually creating threads.
- ✅ Make shared data **immutable** wherever possible.
- ✅ Use **ConcurrentHashMap**, **CopyOnWriteArrayList**, **BlockingQueue** for thread-safe collections.
- ✅ Use **ReentrantLock** when you need advanced lock control.
- ✅ Monitor thread pools carefully (Thread Dump analysis).
- ✅ Handle InterruptedException properly.
- ✅ Always **shutdown ExecutorService** properly.

---

## 📘 Cheat Sheet Summary

- `Runnable` → No return value
- `Callable` → Returns a value, can throw checked exceptions
- `ExecutorService` → Manages lifecycle of threads
- `CountDownLatch`, `CyclicBarrier` → For coordination between threads
- `ForkJoinPool` → Best for divide-and-conquer recursive tasks (like parallel array sort)

---

## 🔗 Extras

- [Java Concurrency API Guide](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/package-summary.html)
- [Java Thread and Concurrency Interview Questions](https://www.baeldung.com/java-concurrency-interview-questions)

---
