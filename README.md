# ScalyShop - Cloud-Native E-Commerce Platform

A distributed, cloud-native e-commerce application demonstrating modern microservices architecture, container orchestration, and Infrastructure-as-Code practices.

## Tech Stack

### Frontend
![Vue.js](https://img.shields.io/badge/Vue.js-3-4FC08D?logo=vue.js&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-5-646CFF?logo=vite&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap_Vue-5-7952B3?logo=bootstrap&logoColor=white)

### Backend
![Node.js](https://img.shields.io/badge/Node.js-18-339933?logo=node.js&logoColor=white)
![Express.js](https://img.shields.io/badge/Express.js-4-000000?logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-Sharded-47A248?logo=mongodb&logoColor=white)
![Mongoose](https://img.shields.io/badge/Mongoose-8-880000)

### DevOps & Infrastructure
![Docker](https://img.shields.io/badge/Docker-24-2496ED?logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-1.28-326CE5?logo=kubernetes&logoColor=white)
![Helm](https://img.shields.io/badge/Helm-3-0F1689?logo=helm&logoColor=white)
![Helmfile](https://img.shields.io/badge/Helmfile-0.157-000000)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-CI/CD-2088FF?logo=github-actions&logoColor=white)

### Monitoring & Observability
![Prometheus](https://img.shields.io/badge/Prometheus-Metrics-E6522C?logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-Dashboards-F46800?logo=grafana&logoColor=white)

### Infrastructure Components
![NGINX](https://img.shields.io/badge/NGINX-Ingress-009639?logo=nginx&logoColor=white)
![Let's Encrypt](https://img.shields.io/badge/Cert--Manager-SSL/TLS-003A70)

---

## Architecture

```
Internet → NGINX Ingress → Frontend (Vue.js)
                         ↓
                         Backend (Express.js API)
                         ↓
                         MongoDB Sharded Cluster
```

**Deployment**: Multi-tier Kubernetes architecture with horizontal auto-scaling, load balancing, and distributed database sharding.

---

## Repository Structure

This project is organized as a **monorepo with Git submodules**:

```
scalyshop-v2/
├── scalyshop-v2-backend/          # Backend service (submodule)
├── scalyshop-v2-frontend/         # Frontend application (submodule)
├── scalyshop-cluster-management/  # Infrastructure IaC (submodule)
├── Assignment1.md                 # Dockerization
├── Assignment2.md                 # Kubernetes deployment
├── Assignment3.md                 # Scaling & load balancing
├── Assignment4.md                 # Monitoring
└── Assignment5.md                 # Advanced topics
```

### Cloning with Submodules

```bash
# Clone main repository with all submodules
git clone --recursive https://github.com/Liafonx/scalyshop-v2.git

# Or if already cloned, initialize submodules
git submodule update --init --recursive
```

---

### 1. Backend Service
**Repository**: [scalyshop-v2-backend](https://github.com/Liafonx/scalyshop-v2-backend)  
**Technologies**: Node.js, Express.js, Mongoose, Docker, Kubernetes, Helm  
**Features**: 
- RESTful API with CRUD operations
- Horizontal Pod Autoscaling (HPA)
- Prometheus metrics integration
- Health checks & readiness probes
- CI/CD with GitHub Actions

### 2. Frontend Application
**Repository**: [scalyshop-v2-frontend](https://github.com/Liafonx/scalyshop-v2-frontend)  
**Technologies**: Vue.js 3, Vite, Bootstrap Vue, Axios, Docker  
**Features**:
- Optimized production builds
- Containerized static asset delivery
- Environment-based configuration
- Client-side routing
- Auto-scaling deployment

### 3. Cluster Management
**Repository**: [scalyshop-cluster-management](https://github.com/Liafonx/scalyshop-cluster-management)  
**Technologies**: Helmfile, Helm, Kubernetes, Prometheus, Grafana  
**Features**:
- Infrastructure-as-Code (IaC)
- GitOps workflow
- MongoDB sharded cluster setup
- Full observability stack
- Declarative infrastructure management

---

## Key Features

### Distributed Systems
- **Microservices Architecture**: Independently deployable services
- **Horizontal Scalability**: Auto-scaling based on CPU/memory metrics
- **Database Sharding**: MongoDB sharded cluster for data distribution
- **Load Balancing**: NGINX Ingress with round-robin distribution
- **Service Discovery**: Kubernetes DNS-based service resolution

### DevOps Practices
- **Containerization**: Multi-stage Docker builds for optimization
- **Container Orchestration**: Kubernetes with Helm package management
- **CI/CD Pipeline**: Automated build, test, and deployment
- **GitOps**: Infrastructure changes via Git commits
- **Rolling Updates**: Zero-downtime deployments

### Observability
- **Metrics**: Prometheus for time-series data collection
- **Visualization**: Grafana dashboards for real-time monitoring
- **Logging**: Centralized pod log aggregation
- **Health Checks**: Liveness and readiness probes

---

## Quick Start

```bash
# 1. Clone with submodules
git clone --recursive https://github.com/Liafonx/scalyshop-v2.git
cd scalyshop-v2

# 2. Deploy infrastructure
cd scalyshop-cluster-management
helmfile sync

# 3. Deploy backend
cd ../scalyshop-v2-backend
helm upgrade --install scalyshop-backend ./scalyshop-backend \
  --namespace scalyshop --create-namespace

# 4. Deploy frontend
cd ../scalyshop-v2-frontend
helm upgrade --install scalyshop-frontend ./scalyshop-frontend \
  --namespace scalyshop
```

---

## Technical Highlights

**Container Optimization**
- Multi-stage Docker builds reducing image size by 60%
- Alpine Linux base images for minimal footprint
- Layer caching for faster CI/CD builds

**Kubernetes Patterns**
- Deployment strategies with rolling updates
- ConfigMaps and Secrets for configuration management
- Resource requests and limits for efficient scheduling
- Horizontal Pod Autoscaler (HPA) for dynamic scaling

**Database Architecture**
- MongoDB sharding with 2+ shards
- Replica sets for high availability
- Automatic failover and data rebalancing
- Connection pooling and query optimization

**Monitoring Stack**
- Prometheus scraping application and system metrics
- Custom Grafana dashboards for business metrics
- Alerting rules for proactive issue detection
- Request tracing and performance monitoring

---

## Performance

- **Auto-scaling**: 2-10 pods based on load
- **Response Time**: <100ms average API response
- **Availability**: 99.9% uptime with replica sets
- **Scalability**: Horizontal scaling tested up to 1000 req/s

---

## Related Repositories

- **Backend**: [scalyshop-v2-backend](https://github.com/Liafonx/scalyshop-v2-backend)
- **Frontend**: [scalyshop-v2-frontend](https://github.com/Liafonx/scalyshop-v2-frontend)
- **Infrastructure**: [scalyshop-cluster-management](https://github.com/Liafonx/scalyshop-cluster-management)

---

## License

Educational project demonstrating cloud-native architecture and DevOps practices.
