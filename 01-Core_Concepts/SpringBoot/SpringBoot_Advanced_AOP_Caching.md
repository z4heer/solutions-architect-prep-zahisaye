# 📚 Spring Boot Advanced: AOP and Caching

In real-world architectures, **cross-cutting concerns** like logging, security, and caching are crucial. Spring Boot provides **AOP (Aspect-Oriented Programming)** and **Caching** support to simplify these.

---

## 🧠 Mind Map

```
Spring Boot AOP & Caching
├── Aspect-Oriented Programming (AOP)
│   ├── @Aspect
│   ├── @Before
│   ├── @AfterReturning
│   ├── @Around
│   └── Pointcuts
├── Spring Boot Caching
│   ├── @EnableCaching
│   ├── @Cacheable
│   ├── @CacheEvict
│   ├── Redis Cache
│   └── Ehcache
├── Performance Tuning
├── Error Handling
```

---

## 📚 Key Technical Words & Definitions

| Term | Definition |
|------|------------|
| **AOP** | Programming paradigm to separate cross-cutting concerns (e.g., logging, security). |
| **Aspect** | A class that contains advice (actions) and pointcuts (where advice is applied). |
| **Pointcut** | An expression that matches certain join points (method executions). |
| **Advice** | Code executed at a join point (before, after, around). |
| **@Cacheable** | Caches the result of a method invocation. |
| **@CacheEvict** | Removes an entry from the cache. |
| **Ehcache** | Popular Java-based cache used for local caching. |
| **Redis** | In-memory data structure store used for distributed caching. |

---

## 🔎 Common Interview Questions

- How does AOP work internally in Spring?
- What's the difference between `@Around`, `@Before`, and `@AfterReturning`?
- How is caching implemented in Spring Boot?
- Which cache would you use for distributed architecture?
- How would you invalidate or evict cached data?

---

## 🧪 Code Snippets

### ✅ AOP Example: Logging All Service Methods
```java
@Aspect
@Component
public class LoggingAspect {

    @Before("execution(* com.example.service.*.*(..))")
    public void logBefore(JoinPoint joinPoint) {
        System.out.println("Executing: " + joinPoint.getSignature().getName());
    }
}
```

### ✅ Enable Caching
```java
@SpringBootApplication
@EnableCaching
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}
```

### ✅ Simple Caching Example
```java
@Service
public class ProductService {

    @Cacheable("products")
    public Product getProductById(Long id) {
        // Simulate DB access
        return productRepository.findById(id).orElseThrow();
    }
}
```

### ✅ Evict Cache on Update
```java
@CacheEvict(value = "products", key = "#product.id")
public Product updateProduct(Product product) {
    return productRepository.save(product);
}
```

---

## 🎯 Best Practices Summary

- ✅ Use AOP for cross-cutting concerns like logging, security, and transaction management.
- ✅ Annotate main class with `@EnableCaching`.
- ✅ Choose Redis for distributed caching, Ehcache for local single-instance caching.
- ✅ Properly configure cache TTL (Time-to-Live).
- ✅ Monitor cache hit/miss statistics for optimization.

---

## 📘 Cheat Sheet Summary

| Topic | Summary |
|-------|---------|
| AOP Annotations | `@Aspect`, `@Before`, `@After`, `@Around` |
| Caching Annotations | `@Cacheable`, `@CacheEvict`, `@CachePut` |
| Pointcut Expression | `execution(* package.name.*.*(..))` |
| Local Cache | Ehcache, Caffeine |
| Distributed Cache | Redis, Hazelcast |

---

## ⚠️ Common Mistakes

| Mistake | Why Avoid |
|---------|-----------|
| Overusing AOP | Harder to debug and trace program flow. |
| Uncontrolled Cache Growth | Can lead to memory leaks. |
| Missing Cache Invalidation | Causes stale data issues. |
| Caching Sensitive Data | Can cause security vulnerabilities. |
| Poor TTL Configuration | Increases cache misses or stale cache issues. |

---

## 🔗 Extras

- [Baeldung - Spring AOP Tutorial](https://www.baeldung.com/spring-aop)
- [Baeldung - Spring Caching Guide](https://www.baeldung.com/spring-cache-tutorial)
- [Spring Docs - Cache Abstraction](https://docs.spring.io/spring-framework/docs/current/reference/html/integration.html#cache)

---
