# 🧪 Testing - Mind Map

---

## 🔹 Core Concepts
- **Unit Testing**: Testing individual units/components of code.
- **Integration Testing**: Testing interaction between components.
- **API Testing**: Verifying APIs for functionality, reliability, performance.

---

## 🛠️ Key Technical Words
| Term | Definition |
|:---|:---|
| JUnit | Java framework for writing repeatable unit tests. |
| Mockito | Mocking framework for unit tests in Java. |
| Postman | Tool for API development, testing, and monitoring. |
| Assertion | Statement that checks if a condition is true. |
| Mocking | Creating fake objects to simulate real behavior. |

---

## 🛠️ JUnit
- **JUnit 5 Structure**:
  - `@Test` → Marks a method as a test case.
  - `@BeforeEach` / `@AfterEach` → Setup and teardown.
  - `@BeforeAll` / `@AfterAll` → Class-level setup and teardown.

- **Common Assertions**:
  ```java
  assertEquals(expected, actual);
  assertTrue(condition);
  assertNotNull(object);
  ```

- **Example**:
  ```java
  @Test
  void additionShouldBeCorrect() {
      assertEquals(2, 1 + 1);
  }
  ```

---

## 🛠️ Mockito
- **Mock Object**:
  ```java
  MyService service = mock(MyService.class);
  ```

- **Stubbing Behavior**:
  ```java
  when(service.getData()).thenReturn("Mocked Data");
  ```

- **Verifying Interactions**:
  ```java
  verify(service).getData();
  ```

- **Useful Annotations**:
  - `@Mock`, `@InjectMocks`

---

## 🛠️ Postman for API Testing
- **Create Collections**: Organize your APIs logically.
- **Environment Variables**: Manage base URLs, tokens.
- **Pre-Request Scripts**: Setup conditions before API calls.
- **Tests Tab**: Write JavaScript assertions.
  
- **Basic API Test Example**:
  ```javascript
  pm.test("Status code is 200", function () {
      pm.response.to.have.status(200);
  });
  ```

- **Automation**: Use Newman to run Postman collections from CLI.

---

## 🎯 Best Practices
- Write meaningful test case names.
- Test one condition per test.
- Mock external services instead of hitting real endpoints.
- Maintain clean separation between Unit and Integration Tests.
- Use environment variables in Postman.

---

## ❓ Common Interview Questions
- How is JUnit 5 different from JUnit 4?
- What are mocks and spies in Mockito?
- How do you validate authentication flows in Postman?
- Difference between unit test and integration test?

---

## 📋 Cheat Sheet
| Area | Quick Tip |
|:---|:---|
| JUnit | Unit tests for Java methods |
| Mockito | Mock dependencies to isolate tests |
| Postman | Automate and validate API endpoints |

---

## ⚡ Common Mistakes
- Writing too many assertions in a single test.
- Not cleaning up resources between tests.
- Over-mocking which leads to meaningless tests.
- Ignoring error-handling scenarios in API tests.

---
