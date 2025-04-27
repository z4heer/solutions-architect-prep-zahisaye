# 🛡️ Security Concepts - Mind Map

---

## 🔹 Core Concepts
- **Authentication (AuthN)**: Verifying *who* you are.
- **Authorization (AuthZ)**: Verifying *what* you are allowed to do.
- **JWT (JSON Web Token)**: Securely transmits user info between parties.
- **OAuth 2.0**: Delegated authorization framework.

---

## 🛠️ Key Technical Words
| Term | Definition |
|:---|:---|
| Authentication | Process of confirming user identity. |
| Authorization | Granting access rights based on identity. |
| Token | Small piece of data (e.g., JWT) that authenticates and authorizes. |
| OAuth | Open standard for access delegation without sharing credentials. |
| OpenID Connect | Identity layer on top of OAuth 2.0 for authentication. |

---

## 🛠️ Authentication (AuthN)
- **Credential Verification** (Username/Password, Biometrics).
- **Multi-Factor Authentication (MFA)** improves security.
- **Session-based** vs **Token-based** Authentication.

---

## 🛠️ Authorization (AuthZ)
- **Role-Based Access Control (RBAC)**: Access based on user's role.
- **Attribute-Based Access Control (ABAC)**: Access based on attributes (location, time, etc.).
- **Policy-Based Access Control (PBAC)**: Fine-grained policies.

---

## 🛠️ JWT (JSON Web Token)
- **Three parts**:
  1. **Header** (algorithm & token type)
  2. **Payload** (claims like user ID, roles)
  3. **Signature** (verifies token integrity)

- **JWT Structure**:
  ```
  xxxxx.yyyyy.zzzzz
  ```

- **Sample JWT Payload**:
  ```json
  {
    "sub": "1234567890",
    "name": "John Doe",
    "admin": true
  }
  ```

- **Best Practices**:
  - Always sign JWTs.
  - Keep JWTs short-lived (exp claim).
  - Validate signature at backend.

---

## 🛠️ OAuth 2.0
- **Grant Types**:
  - Authorization Code (most secure, recommended)
  - Client Credentials (for server-to-server)
  - Password Grant (deprecated, discouraged)
  - Implicit Grant (deprecated, discouraged)

- **OAuth Flow**:
  1. User requests access.
  2. Authorization server authenticates user.
  3. Authorization server provides **access token**.
  4. Client uses token to access resource server.

---

## 🎯 Best Practices
- Always encrypt tokens in transit (TLS).
- Use **scoped** access tokens.
- Implement **token expiration** and **refresh tokens** properly.
- Validate input to avoid IDOR (Insecure Direct Object References).

---

## ❓ Common Interview Questions
- Difference between Authentication and Authorization?
- What are JWT pros and cons?
- How does OAuth 2.0 Authorization Code flow work?
- How to secure REST APIs using OAuth2?

---

## 📋 Cheat Sheet
| Area | Quick Tip |
|:---|:---|
| Authentication | Confirm identity |
| Authorization | Define what user can access |
| JWT | Compact, URL-safe tokens |
| OAuth2 | Delegate authorization securely |

---

## ⚡ Common Mistakes
- Storing sensitive info directly inside JWT.
- Forgetting to validate JWT expiration.
- Using Implicit grant type in OAuth for sensitive apps.
- Not rotating secret keys regularly.

---
