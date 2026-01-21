# 🚀 NodeJS Application Monitoring on Kubernetes
**Prometheus • Grafana • Alertmanager • Slack**

<p align="center">
  <img src="https://img.shields.io/badge/Kubernetes-v1.30-326ce5?logo=kubernetes&logoColor=white" />
  <img src="https://img.shields.io/badge/Prometheus-Monitoring-e6522c?logo=prometheus&logoColor=white" />
  <img src="https://img.shields.io/badge/Grafana-Dashboards-f46800?logo=grafana&logoColor=white" />
  <img src="https://img.shields.io/badge/Docker-Containerization-2496ed?logo=docker&logoColor=white" />
  <img src="https://img.shields.io/badge/Node.js-Application-339933?logo=node.js&logoColor=white" />
</p>

---

## 📖 Table of Contents
- [📌 Project Overview](#-project-overview)
- [🏗️ System Architecture](#️-system-architecture)
- [🛠️ Technologies Used](#️-technologies-used)
- [📂 Project Structure](#-project-structure)
- [🚀 Deployment Guide](#-deployment-guide)
- [📊 Metrics Exposed](#-metrics-exposed)
- [🔔 Alerting Rules](#-alerting-rules)
- [🎯 Why This Project Matters](#-why-this-project-matters)
- [🚀 Future Enhancements](#-future-enhancements)
- [👨‍💻 Author](#-author)

---

## 📌 Project Overview

This project is a **production-oriented DevOps capstone** that demonstrates how to build a **complete monitoring & alerting stack** for a NodeJS application running on Kubernetes.

### Key Capabilities
- 🚀 Deploy a **NodeJS application** on Kubernetes  
- 📊 Expose **custom application metrics** using Prometheus client  
- 📡 Collect **cluster & application metrics** via Prometheus  
- 📈 Visualize metrics using **Grafana dashboards**  
- 🔔 Send alerts to **Slack** using Alertmanager  
- ⚙️ Automate cluster setup using **kubeadm scripts**

> Designed following **real-world observability and SRE best practices**.

---

## 🏗️ System Architecture

### 🔹 High-Level Architecture
![Architecture](architecture/)

### 🔹 screenshots
![ screenshots](screenshots/)


---

## 🛠️ Technologies Used

| Layer | Technology |
|-----|-----------|
| Containerization | Docker |
| Orchestration | Kubernetes (kubeadm) |
| Application | NodeJS (Express) |
| Metrics | Prometheus |
| Visualization | Grafana |
| Alerting | Alertmanager |
| Notifications | Slack Webhook |
| Operating System | Ubuntu Linux |

---

## 📂 Project Structure

```text
nodejs-k8s-monitoring/
├── app/                          # NodeJS application
│   ├── index.js
│   └── Dockerfile
├── k8s/                          # Kubernetes manifests
│   ├── app/
│   │   ├── nodejs-app.yaml
│   │   └── nodejs-svc.yaml
│   └── monitoring/
│       ├── nodejs-monitor-svc.yaml
│       ├── nodejs-rule.yaml
│       ├── nodejs-alert-manager.yaml
│       └── slack-secret-example.yaml
├── scripts/                      # Automation scripts
│   ├── send_requests.sh
│   └── kubeadm/
│       ├── 01-install-k8s-master.sh
│       ├── 02-install-k8s-node1.sh
│       └── 03-install-k8s-node2.sh
├── screenshots/                  # Execution proof
├── architecture/                 # Architecture diagrams
└── README.md
```

---

🚀 Deployment Guide

1️⃣ Kubernetes Cluster Setup (kubeadm)

Run the scripts on each node:

```bash
scripts/kubeadm/01-install-k8s-master.sh
scripts/kubeadm/02-install-k8s-node1.sh
scripts/kubeadm/03-install-k8s-node2.sh
```
---

2️⃣ Build & Push NodeJS Image

```bash
docker build -t <dockerhub-username>/nodejs-app:v1 .
docker push <dockerhub-username>/nodejs-app:v1
```
---

3️⃣ Deploy NodeJS Application

```bash
kubectl apply -f k8s/app/nodejs-app.yaml
kubectl apply -f k8s/app/nodejs-svc.yaml
```
---

4️⃣ Deploy Monitoring Stack

```bash
kubectl apply -f k8s/monitoring/
```
---

5️⃣ Grafana Dashboards

🔹Connect Grafana to Prometheus datasource

🔹Import dashboards:

-Node Metrics

-Pod CPU / Memory

-Application Metrics

---

6️⃣ Alert Testing & Slack Notifications

Generate traffic:

```bash
scripts/send_requests.sh
```

---

📊 Metrics Exposed

🔹 Application Metrics:


-http_requests_root_total

-Default NodeJS process metrics

🔹 Kubernetes Metrics:


-Pod CPU & Memory usage

-Container restarts

-Node resource utilization

---

🔔 Alerting Rules

Example alert rule:

```bash
alert: HighRequestRate_NodeJS
expr: rate(http_requests_root_total[5m]) > 10
```

📢 Sends Slack notification when request rate exceeds threshold.

---

🎯 Why This Project Matters:

✔ Real-world Kubernetes monitoring

✔ Application instrumentation best practices

✔ Alerting & incident awareness

✔ Production-ready DevOps mindset

✔ Clean architecture & documentation

---

🚀 Future Enhancements:


📦 Add Helm charts

📈 Enable HPA using custom metrics

🔐 Add TLS & Ingress

📜 Centralized logging with Loki

---

👨‍💻 Author

Mohanad Faisal
DevOps Engineer
