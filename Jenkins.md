# ✅ Jenkins Hands-On Task List

A comprehensive list of hands-on tasks to master Jenkins and its various capabilities in CI/CD pipelines, automation, integration, and deployment workflows.

---

## 🧱 Jenkins Basics

### 1. Install Jenkins
- Install Jenkins on Ubuntu:
  ```bash
  sudo apt update
  sudo apt install openjdk-11-jdk
  wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
  sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
  sudo apt update
  sudo apt install jenkins
  sudo systemctl start jenkins
  
2. Initial Setup
Access Jenkins: http://<your-server-ip>:8080
Unlock Jenkins using the admin password
Install suggested plugins
Create the first admin user

⚙️ Job Management
3. Create Freestyle Project
Configure Git repo and build shell script

4. Create Pipeline Project
Write a Jenkinsfile:
pipeline {
  agent any
  stages {
    stage('Build') {
      steps { echo 'Building...' }
    }
    stage('Test') {
      steps { echo 'Testing...' }
    }
    stage('Deploy') {
      steps { echo 'Deploying...' }
    }
  }
}


🔄 Source Control Integration
5. GitHub Integration
Install GitHub plugin
Add GitHub PAT as credential
Configure webhook to auto-trigger builds

🧪 Testing & Reporting
6. Run Unit Tests
Use pytest, JUnit, or equivalent
Publish results via JUnit or HTML Publisher plugin

📦 Build Tools Integration
7. Maven & Gradle Integration
Use:
mvn clean install
gradle build

🚀 CI/CD Pipeline
8. Docker Build & Push
Add shell steps to:
docker build -t myapp .
docker push myrepo/myapp

9. Deploy to Kubernetes
Use kubectl:
kubectl apply -f deployment.yaml
10. Deploy to EC2 or VMs
SCP or use Ansible
Use Publish Over SSH plugin

📜 Configuration as Code
11. Multibranch Pipeline
Create pipeline from SCM with a Jenkinsfile per branch

🔐 Credentials and Secrets  
12. Credential Management  
Store secrets via Jenkins Credentials store  
Use in pipeline:  
withCredentials([usernamePassword(credentialsId: 'my-creds', usernameVariable: 'USER', passwordVariable: 'PASS')]) {  
  sh 'curl -u $USER:$PASS https://api.example.com'  
}  

🔔 Notifications  
13. Slack & Email  
Configure Slack plugin with webhook  
Use:  
slackSend channel: '#builds', message: 'Build completed!'  

📈 Monitoring & Scaling  
14. Install Monitoring Plugins  
Use: Monitoring, Performance, Metrics  

15. Master-Agent Setup  
Add agents using SSH/JNLP  
Assign labels and run jobs on agents  

☁️ Jenkins in the Cloud  
16. Docker Jenkins  
Use:  
docker run -p 8080:8080 -p 50000:50000 jenkins/jenkins:lts  

17. Jenkins on Kubernetes  
Use Helm:  
helm repo add jenkins https://charts.jenkins.io  
helm install jenkins jenkins/jenkins  

🧠 Advanced Topics  
19. Shared Libraries  
Create and reference with:  
@Library('shared-lib') _  
mySharedStep()  
20. Parameterized Builds  
Use params.MY_PARAM in Jenkinsfile  

🛡️ Security & Best Practices  
20. Jenkins Hardening  
Use matrix-based security  
Integrate with LDAP or SSO  
Install Role Strategy Plugin  
