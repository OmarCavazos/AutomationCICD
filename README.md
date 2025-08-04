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

```groovy
pipeline {
    agent any

    tools {
        maven 'Maven_3.8.6'   // Name of Maven installed in Jenkins tools config
        jdk 'JDK_11'          // Name of JDK installed in Jenkins tools config
    }

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/your-username/your-repo.git', branch: 'main'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Run Selenium Tests') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Publish Test Results') {
            steps {
                junit '**/test-output/testng-results.xml'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/screenshots/*.png', allowEmptyArchive: true
        }

        failure {
            mail to: 'your-email@example.com',
                 subject: "Build Failed in Jenkins: ${env.JOB_NAME}",
                 body: "Check Jenkins for details: ${env.BUILD_URL}"
        }
    }
}

    📝 Make sure your Jenkins tools (JDK & Maven) are named correctly in Jenkins → Global Tool Configuration.

✅ Running Locally

git clone https://github.com/your-username/your-repo.git
cd your-repo
mvn clean test

📌 Tips

    Include your WebDriver binaries in /drivers/ or configure them via WebDriverManager.

    Store sensitive data (like credentials) in Jenkins Credentials Manager.

    Use Jenkins Shared Libraries for reusable pipeline logic (advanced).

✍️ Author

Omar Cavazos
