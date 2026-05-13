# DevOps CI/CD Monitoring Project

## Project Overview

This project demonstrates a complete DevOps CI/CD pipeline using Docker, Jenkins, GitHub, Prometheus, and Grafana inside an Ubuntu Virtual Machine environment.

The application is a simple Flask web application containerized using Docker and automatically deployed through a Jenkins pipeline after pulling code from GitHub.

The project also includes a monitoring stack using Prometheus and Grafana for real-time system monitoring and observability.

---

# Architecture

```text
GitHub
   ↓
Jenkins CI/CD Pipeline
   ↓
Docker Build & Deployment
   ↓
Flask Web Application
   ↓
Prometheus Monitoring
   ↓
Grafana Dashboards
```

---

# Technologies Used

| Tool          | Purpose                         |
| ------------- | ------------------------------- |
| Ubuntu 22.04  | Development Environment         |
| Docker        | Containerization                |
| Jenkins       | CI/CD Automation                |
| GitHub        | Version Control                 |
| Flask         | Python Web Application          |
| Prometheus    | Monitoring & Metrics Collection |
| Grafana       | Visualization Dashboard         |
| Node Exporter | System Metrics Exporter         |
| VirtualBox    | Virtual Machine Platform        |

---

# Features

* Dockerized Flask application
* Jenkins automated CI/CD pipeline
* GitHub integration for source control
* Automated Docker image build and deployment
* Monitoring using Prometheus
* Visualization using Grafana dashboards
* Linux-based DevOps environment
* Containerized infrastructure

---

# Project Setup

## 1. Clone Repository

```bash
git clone https://github.com/Neelakantha618/devops-ci-cd-project.git
cd devops-ci-cd-project
```

---

## 2. Build Docker Image

```bash
docker build -t flask-app .
```

---

## 3. Run Flask Container

```bash
docker run -d --name flask-container -p 5001:5000 flask-app
```

---

# Jenkins CI/CD Pipeline

The Jenkins pipeline performs the following tasks:

1. Pull source code from GitHub
2. Build Docker image
3. Stop old container
4. Deploy updated container automatically

## Jenkins Pipeline Script

```groovy
pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Neelakantha618/devops-ci-cd-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop flask-container || true'
                sh 'docker rm flask-container || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d --name flask-container -p 5001:5000 flask-app'
            }
        }
    }
}
```

---

# Monitoring Stack

The project uses Prometheus and Grafana for monitoring and observability.

## Docker Compose Services

* Prometheus
* Grafana
* Node Exporter

## Start Monitoring Stack

```bash
docker-compose up -d
```

---

# Prometheus Configuration

```yaml
global:
  scrape_interval: 5s

scrape_configs:
  - job_name: 'node-exporter'
    static_configs:
      - targets: ['node-exporter:9100']
```

---

# Grafana Dashboard

Grafana is configured with Prometheus as the datasource.

Dashboard ID used:

```text
1860
```

This dashboard displays:

* CPU Usage
* Memory Usage
* Disk Usage
* Network Metrics
* System Performance Metrics

---

# Screenshots

## Jenkins Pipeline

*Add Jenkins pipeline screenshot here*

## Grafana Dashboard

*Add Grafana dashboard screenshot here*

## Docker Containers

*Add docker ps screenshot here*

## Flask Application

*Add Flask application screenshot here*

---

# Future Improvements

* Kubernetes Deployment
* GitHub Webhooks
* AWS Cloud Deployment
* Terraform Infrastructure Automation
* SonarQube Integration
* Nginx Reverse Proxy
* SSL/HTTPS Configuration

---

# Learning Outcomes

Through this project, the following DevOps concepts were implemented and understood:

* CI/CD Pipeline Automation
* Docker Containerization
* Linux Administration
* Git & GitHub Workflow
* Jenkins Pipeline Configuration
* Monitoring and Observability
* Infrastructure Management
* DevOps Workflow Automation

---

# Author

Neelakantha Pandurang Kamat Nilkundkar

GitHub: [https://github.com/Neelakantha618](https://github.com/Neelakantha618)
