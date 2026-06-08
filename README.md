# Trend DevOps Project

## Project Overview

This project demonstrates a complete DevOps implementation for the Trend application using AWS, Terraform, Docker, Jenkins, GitHub, and Kubernetes (EKS).

The objective was to automate infrastructure provisioning, containerization, CI/CD deployment, and monitoring of the application.

---

## Architecture

GitHub Repository
↓
GitHub Webhook
↓
Jenkins Pipeline
↓
Docker Build
↓
DockerHub Push
↓
Amazon EKS Deployment
↓
Application Access via LoadBalancer

---

## Technologies Used

* AWS EC2
* Amazon EKS
* Docker
* DockerHub
* Jenkins
* GitHub
* Terraform
* Kubernetes
* CloudWatch

---

## Repository

GitHub:
https://github.com/Radha96dev/Trend

DockerHub:
https://hub.docker.com/repository/docker/radha96/trend-app

---

## Infrastructure Provisioning

Terraform was used to provision the required AWS infrastructure.

Commands:

terraform init

terraform plan

terraform apply

---

## Docker Containerization

Build Docker Image:

docker build -t trend-app .

Tag Image:

docker tag trend-app radha96/trend-app:latest

Push Image:

docker push radha96/trend-app:latest

---

## Jenkins CI/CD Pipeline

Pipeline Stages:

1. Clone Source Code
2. Build Docker Image
3. Push Image to DockerHub
4. Deploy Application to EKS
5. Verify Deployment

GitHub webhook was configured to automatically trigger Jenkins builds on code commits.

---

## Kubernetes Deployment

Deployment was performed on Amazon EKS using Kubernetes manifests.

Commands:

kubectl apply -f deployment.yaml

kubectl apply -f service.yaml

Verification:

kubectl get pods

kubectl get svc

---

## Monitoring

Monitoring was performed using AWS CloudWatch and Kubernetes monitoring tools.

Application logs and deployment status were continuously monitored.

---

## Screenshots

Included:

* GitHub Repository
* DockerHub Repository
* Terraform Apply Output
* Jenkins Dashboard
* Jenkins Successful Build
* GitHub Webhook Delivery
* EKS Cluster
* Kubernetes Pods
* Kubernetes Services
* Application Running
* Monitoring Dashboard

---

## Cleanup

To avoid AWS charges, resources were removed after project completion.

Examples:

eksctl delete cluster --name <cluster-name> --region ap-south-1

terraform destroy

Delete Load Balancers

Delete ECR Repositories

Delete CodeBuild Projects

Delete CodePipeline Resources

Delete EC2 Instances

---


Radhamani R
DevOps Project Submission
