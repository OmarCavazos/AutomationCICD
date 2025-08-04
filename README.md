Selenium Java CI/CD Pipeline using GitHub + Jenkins + Maven

This project demonstrates a complete CI/CD pipeline for automated UI testing using **Selenium WebDriver with Java and TestNG**, integrated with **GitHub** and **Jenkins Declarative Pipelines**.

---

## 🧱 Project Structure

📁 src/
├── main/java/ # Page Object classes (POM)
├── test/java/ # Test cases
📄 testng.xml # TestNG suite config
📄 pom.xml # Maven build config
📄 Jenkinsfile # CI/CD pipeline definition


---

## 🧰 Tech Stack

- **Language:** Java  
- **Automation Framework:** Selenium WebDriver + TestNG  
- **Build Tool:** Maven  
- **CI/CD:** Jenkins  
- **Version Control:** GitHub

---

## 🔁 CI/CD Flow Overview

1. Developer pushes code to GitHub.
2. GitHub webhook notifies Jenkins.
3. Jenkins pulls the code and executes the Maven build.
4. Selenium tests run automatically via TestNG.
5. Test results are published in Jenkins.

---

## 📄 Jenkinsfile (Declarative Pipeline)
