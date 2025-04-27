# 🧠 DevOps & CI/CD Basics - Mind Map

---

## 🔹 Core Concepts
- **CI/CD**: Continuous Integration / Continuous Deployment
- **Automation**: Automate build, test, and deployment.
- **Containerization**: Package apps using Docker.
- **Orchestration**: Manage containers with Kubernetes.

---

## 🛠️ Key Technical Words
| Term | Definition |
|:---|:---|
| CI | Frequently merging code to main branch. |
| CD | Automatically deploying every code change. |
| Pipeline | A series of steps for building, testing, deploying. |
| Container | Lightweight, standalone executable package (e.g., Docker container). |
| Orchestration | Managing and scaling containers (e.g., Kubernetes). |

---

## 🛠️ Jenkins Basics
- Open-source automation server.
- Supports building, testing, and deploying pipelines.
- Integrates with almost every tool (GitHub, Docker, Kubernetes).

**Common Jenkins Components**:
- **Job**: A runnable task.
- **Pipeline**: Automated series of steps.
- **Agent**: A machine to run the job.

---

## 🛠️ Docker Basics
- Package application + dependencies into containers.
- **Dockerfile** ➔ Blueprint to build containers.
- **docker-compose.yml** ➔ Define and run multi-container apps.

**Common Commands**:
```bash
docker build -t myapp .
docker run -p 3000:3000 myapp
docker-compose up
```

---

## 🛠️ Kubernetes Basics
- Container orchestration platform.
- **Pod** ➔ Smallest unit (one or more containers).
- **Service** ➔ Expose Pods to network.
- **Deployment** ➔ Manage scaling and updates.

**Common Commands**:
```bash
kubectl get pods
kubectl apply -f deployment.yaml
kubectl scale deployment myapp --replicas=3
```

---

## 🛠️ GitHub Actions Basics
- Native CI/CD automation inside GitHub.
- Workflow defined by **.github/workflows/** folder.

**Sample Workflow (Node.js app)**:
```yaml
name: Node.js CI
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Set up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '16'
      - run: npm install
      - run: npm test
```

---

## 🎯 Best Practices
- Use environment-specific variables in pipelines.
- Secure secrets (e.g., GitHub Secrets, Jenkins Credentials).
- Monitor pipeline health (failures, flakiness).
- Regularly update base Docker images.

---

## ❓ Common Interview Questions
- What is the difference between Docker and Kubernetes?
- How would you design a scalable CI/CD pipeline?
- How do you handle secrets in Jenkins and GitHub Actions?

---

## 📋 Cheat Sheet
| Tool | Purpose |
|:---|:---|
| Jenkins | Build/Test/Deploy Automation |
| Docker | Containerization |
| Kubernetes | Container orchestration |
| GitHub Actions | Native CI/CD in GitHub |

---

## ⚡ Common Mistakes
- Ignoring rollback strategies.
- No image version tagging ➔ hard to track deployments.
- Overcomplicating Kubernetes YAMLs.

---
