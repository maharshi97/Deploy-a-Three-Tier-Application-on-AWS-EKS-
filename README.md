# Ultimate DevOps & SRE Project: Cloud-Native Microservices on AWS EKS

![Project Status](https://img.shields.io/badge/status-active-success)
![Kubernetes](https://img.shields.io/badge/kubernetes-%23326ce5.svg?style=flat&logo=kubernetes&logoColor=white)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=flat&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=flat&logo=amazon-aws&logoColor=white)
![OpenTelemetry](https://img.shields.io/badge/OpenTelemetry-000000?style=flat&logo=opentelemetry&logoColor=white)

## 🚀 Project Overview

This repository demonstrates a comprehensive implementation of modern **DevOps** and **Site Reliability Engineering (SRE)** practices. It features a complex, cloud-native **polyglot microservices application** (based on the OpenTelemetry Astronomy Shop) deployed on **Amazon EKS (Elastic Kubernetes Service)**.

The primary goal of this project was to simulate a real-world production environment to learn and master the full lifecycle of cloud-native applications—from containerization and orchestration to advanced observability and automated deployments.

## 🏗️ Architecture

The application is an E-commerce platform built using a **Microservices Architecture**. It consists of **10+ services**, each written in a different programming language to demonstrate polyglot support and service interoperability using **gRPC** and **Protobuf**.

### Service Stack
| Service | Language/Tech | Description |
|---------|--------------|-------------|
| **Frontend** | Next.js / TypeScript | Web interface for the shop. |
| **Ad Service** | Java | Provides text advertisements based on context keys. |
| **Cart** | C# / .NET | Manages users' shopping carts (Redis backed). |
| **Checkout** | Go | Retrieves cart, prepares order, charges card, ships. |
| **Currency** | C++ | Converts currency values. |
| **Email** | Ruby | Sends order confirmation emails. |
| **Payment** | Node.js | Charges credit cards. |
| **Product Catalog** | Go | Provides list of products from JSON. |
| **Quote** | PHP | Calculates shipping costs. |
| **Recommendation** | Python | Recommends products based on what's in the cart. |
| **Shipping** | Rust | Gives shipping cost estimates and tracking IDs. |

### Infrastructure & Tools
- **Containerization:** Docker & Docker Compose
- **Orchestration:** Kubernetes (AWS EKS)
- **CI/CD:** GitHub Actions (Automated testing and deployment)
- **Service Mesh / Networking:** Envoy Proxy
- **Databases/Cache:** PostgreSQL, Redis, Kafka

## 📊 SRE & Observability

A major focus of this project is **Observability**. The application is fully instrumented with **OpenTelemetry** to provide end-to-end visibility into the distributed system.

- **Tracing:** Jaeger (End-to-end distributed tracing).
- **Metrics:** Prometheus (Scraping service metrics).
- **Visualization:** Grafana (Dashboards for Infrastructure & Application metrics).
- **Logging:** OpenSearch / Fluent Bit.
- **Load Testing:** Locust (to simulate user traffic and generate telemetry data).

## 🛠️ Concepts Learned & Implemented

1.  **Microservices Patterns**: Handling service-to-service communication via gRPC, fault tolerance, and independent scaling.
2.  **Containerization**: Writing optimized `Dockerfile`s for multiple languages and managing multi-container setups with `docker-compose`.
3.  **Kubernetes Orchestration**:
    -   Writing declarative K8s manifests (`Deployment`, `Service`, `Ingress`, `ConfigMap`, `Secret`).
    -   Managing application lifecycle on EKS.
4.  **DevOps Pipeline**:
    -   Building automated workflows in GitHub Actions.
    -   Linting, Testing, and Building container images.
5.  **Observability Strategy**:
    -   Implementing the "Three Pillars of Observability" (Logs, Metrics, Traces).
    -   Debugging performance bottlenecks using customized Grafana dashboards and Jaeger traces.

## 🚀 Getting Started

### Prerequisites
- Docker & Docker Desktop
- Kubernetes CLI (`kubectl`)
- AWS CLI (configured)

### Local Deployment (Docker Compose)
To run the application locally without Kubernetes:
```bash
docker-compose up -d
```
Access the frontend at `http://localhost:8080`.

### Kubernetes Deployment
1. **Provision an EKS Cluster** (using `eksctl` or Terraform).
2. **Apply Manifests**:
```bash
kubectl apply -f kubernetes/
```
3. **Port Forwarding** (to access locally):
```bash
kubectl port-forward svc/frontendproxy 8080:8080
```

## 📈 Future Improvements
- Implement **Terraform** for full Infrastructure as Code (IaC) provisioning.
- Add **ArgoCD** for GitOps deployments.
- Implement **Istio** Service Mesh for advanced traffic management/canary deployments.
- Add **Chaos Engineering** experiments to test resilience.

---
*Created by [Maharshi](https://github.com/maharshi97) as a capstone project for DevOps & SRE mastery.*
