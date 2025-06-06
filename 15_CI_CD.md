# Day-18

## 🔁 **What is CI/CD?**

* **CI (Continuous Integration)**: Developers frequently merge code into a shared repository. Each merge triggers automated builds and tests to detect issues early.
* **CD (Continuous Delivery/Deployment)**:

  * **Continuous Delivery**: Ensures that the codebase is always in a deployable state, and deployment is triggered **manually**.
  * **Continuous Deployment**: Goes one step further — every change that passes automated tests is **automatically deployed** to production.

---

## ✅ **Benefits of CI/CD**

* Faster delivery of features and fixes.
* Early detection of bugs.
* Reliable and repeatable deployment process.
* Increased developer confidence and team productivity.

---

## 🔧 **CI/CD Pipeline Stages**

A typical CI/CD pipeline has the following stages:

### 1. **Source Code Management**

* Tools: Git, GitHub, GitLab, Bitbucket.
* Developers push code changes to a shared repository.

### 2. **Build**

* The code is compiled or packaged.
* Tools: Maven, Gradle, npm, Docker.
* Ensures the code can be built correctly.

### 3. **Automated Testing**

* Unit tests, integration tests, UI tests.
* Tools: JUnit, Selenium, PyTest, Jest.
* Ensures functionality and detects bugs early.

### 4. **Code Analysis**

* Static code analysis for bugs, vulnerabilities, and styling issues.
* Tools: SonarQube, ESLint, PMD.

### 5. **Artifact Storage**

* Built packages or containers are stored.
* Tools: JFrog Artifactory, Nexus, Docker Hub.

### 6. **Deployment**

* Deploy to staging or production environments.
* Tools: Jenkins, GitHub Actions, GitLab CI/CD, Azure DevOps, CircleCI.

### 7. **Monitoring and Feedback**

* Logs and metrics are monitored to ensure stability.
* Tools: Prometheus, Grafana, ELK Stack, Splunk.

---

## 🔄 **Difference between Continuous Delivery vs Continuous Deployment**

| Feature    | Continuous Delivery           | Continuous Deployment         |
| ---------- | ----------------------------- | ----------------------------- |
| Deployment | Manual (but ready anytime)    | Fully automated               |
| Risk       | Lower (human review possible) | Requires high test confidence |
| Speed      | Fast                          | Fastest                       |
| Control    | More                          | Less                          |

---

## 🛠️ **Popular CI/CD Tools**

| Category         | Tools                                        |
| ---------------- | -------------------------------------------- |
| CI/CD Servers    | Jenkins, GitHub Actions, GitLab CI, CircleCI |
| Containerization | Docker, Podman                               |
| Orchestration    | Kubernetes, OpenShift                        |
| Deployment       | Helm, Ansible                                |
| Monitoring       | Prometheus, Grafana, Datadog                 |

---

## 🧠 **Real-World Example**

Let’s say you're building a web app:

1. You push your code to GitHub.
2. GitHub Actions starts running:

   * It builds the app using npm.
   * It runs unit and integration tests.
3. If all tests pass, it creates a Docker image and stores it in Docker Hub.
4. In Continuous Delivery:

   * You get a button to manually deploy to production.
5. In Continuous Deployment:

   * It automatically deploys the new version to your cloud server (e.g., AWS, Azure).

---

## 📌 Summary

| Term            | Description                                                 |
| --------------- | ----------------------------------------------------------- |
| CI              | Automatically build and test code whenever it's pushed.     |
| CD (Delivery)   | Code is always ready for deployment, but deployed manually. |
| CD (Deployment) | Code is deployed automatically after passing tests.         |

---


