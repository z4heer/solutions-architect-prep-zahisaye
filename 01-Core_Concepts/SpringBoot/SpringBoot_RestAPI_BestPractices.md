Perfect, let's keep going! 🚀  
Here’s the next detailed file:

---

### ✅ `01-Core_Concepts/SpringBoot/SpringBoot_RestAPI_BestPractices.md`

```markdown
# 📚 Spring Boot REST API Best Practices

Building production-grade, scalable, and maintainable REST APIs is critical for Solutions Architect roles.

---

## 🧠 Mind Map

```
REST API Best Practices
├── HTTP Status Codes
├── Consistent JSON Response
├── Exception Handling
├── Validation
├── Logging
├── Pagination
├── HATEOAS (optional)
├── Security (JWT, OAuth2)
├── OpenAPI/Swagger Documentation
```

---

## 📚 Key Technical Words & Definitions

| Term | Definition |
|------|------------|
| **REST** | Representational State Transfer; architecture style for designing networked applications. |
| **DTO** | Data Transfer Object; used to transfer data without exposing internal entities. |
| **Exception Handling** | Handling errors gracefully and returning meaningful responses. |
| **Pagination** | Dividing large results into smaller chunks for efficient data transfer. |
| **Validation** | Ensuring incoming request data adheres to expected format and rules. |
| **JWT** | JSON Web Token; a compact, URL-safe token used for authentication. |
| **Swagger/OpenAPI** | API documentation and exploration tool. |

---

## 🔎 Common Interview Questions

- How do you design a scalable REST API?
- How to handle exceptions globally in Spring Boot?
- Why use DTOs instead of directly returning entities?
- How would you secure a REST API?
- What are HTTP best practices for REST APIs?

---

## 🧪 Code Snippets

### ✅ Simple Controller
```java
@RestController
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{id}")
    public ResponseEntity<UserDTO> getUser(@PathVariable Long id) {
        return ResponseEntity.ok(userService.findById(id));
    }
}
```

### ✅ Global Exception Handling
```java
@RestControllerAdvice
public class GlobalExceptionHandler {

    @ExceptionHandler(ResourceNotFoundException.class)
    public ResponseEntity<ErrorResponse> handleNotFound(ResourceNotFoundException ex) {
        ErrorResponse error = new ErrorResponse("NOT_FOUND", ex.getMessage());
        return new ResponseEntity<>(error, HttpStatus.NOT_FOUND);
    }
}
```

### ✅ Standard API Response Structure
```json
{
  "timestamp": "2025-04-26T12:00:00",
  "status": 200,
  "message": "Success",
  "data": {
    "userId": 1,
    "username": "john_doe"
  }
}
```

---

## 🎯 Best Practices Summary

- ✅ Always use meaningful HTTP status codes (`200 OK`, `201 Created`, `404 Not Found`, `500 Internal Server Error`).
- ✅ Use DTOs to avoid exposing internal database entities.
- ✅ Implement global exception handling with `@ControllerAdvice`.
- ✅ Validate input with `@Valid` and `@Validated`.
- ✅ Secure APIs with JWT/OAuth2 tokens.
- ✅ Document APIs with OpenAPI/Swagger.

---

## 📘 Cheat Sheet Summary

| Topic | Summary |
|-------|---------|
| HTTP Codes | `200 OK`, `201 Created`, `204 No Content`, `400 Bad Request`, `404 Not Found`, `500 Internal Server Error`. |
| Validation | Use `@NotNull`, `@Size`, `@Email`, etc. for input validation. |
| Exception Handling | Centralized with `@ControllerAdvice`. |
| Pagination | Use `Pageable` interface and `Page` object from Spring Data JPA. |
| API Documentation | Swagger UI auto-generates interactive API documentation. |

---

## ⚠️ Common Mistakes

| Mistake | Why Avoid |
|---------|-----------|
| Returning raw Entities | Leads to security risks and unnecessary data exposure. |
| Improper HTTP Status codes | Confuses clients and leads to poor API design. |
| No input validation | Vulnerable to malformed requests and attacks. |
| Inconsistent error responses | Makes debugging difficult for API consumers. |
| Lack of documentation | Hard for other teams to use your APIs. |

---

## 🔗 Extras

- [Building a RESTful Web Service with Spring Boot](https://spring.io/guides/gs/rest-service/)
- [Baeldung - Spring REST API Best Practices](https://www.baeldung.com/rest-api-spring-oauth2-angular)

---

📌 **Next Recommendation**: Master `SpringBoot_Security_JWT.md` to learn real-world authentication and authorization using Spring Security with JWT!
```
