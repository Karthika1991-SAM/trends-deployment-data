# Trend App – CI/CD Deployment using DevOps 🚀

This project demonstrates how to deploy a **React application** into a **production-ready environment** using **Docker, Jenkins, Terraform, and AWS EKS** with a complete **CI/CD pipeline**.

---

## 📌 Project Objective
- Deploy a React application on **AWS EKS**
- Automate build, push, and deployment using **Jenkins**
- Use **DockerHub** for image storage
- Provision infrastructure using **Terraform**
- Enable **GitHub Webhook** for auto-triggered builds

---

## 🛠️ Tools & Technologies
- **React**
- **Docker**
- **Jenkins (Declarative Pipeline)**
- **Terraform**
- **AWS (EC2, EKS, IAM, ELB)**
- **Kubernetes**
- **DockerHub**
- **GitHub**

---

## 📂 Project Structure
.
├── Dockerfile
├── Jenkinsfile
├── deployment.yaml
├── service.yaml
├── terraform/
├── package.json
├── README.md

---

🔁 Jenkins CI/CD Pipeline

The Jenkins pipeline performs the following steps automatically:

Checkout code from GitHub

Build Docker image

Push image to DockerHub

Deploy application to AWS EKS using kubectl

Pipeline configuration is defined in the Jenkinsfile.

🔗 GitHub Webhook

GitHub webhook is configured with Jenkins

Every push to the main branch triggers the pipeline automatically
After deployment, the application is exposed using a LoadBalancer service.

Access the app in browser:

http://aeb47fcfc9a7d44f394581a3c8268b4f-1096532754.ap-south-1.elb.amazonaws.com

Cluster and application health can be monitored using:

kubectl commands

Prometheus & Grafana 





---

## 👤 Author
**Karthika Rajendran**

