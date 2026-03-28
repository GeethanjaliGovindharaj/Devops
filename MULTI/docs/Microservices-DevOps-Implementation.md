# Microservices DevOps Implementation

## Overview
This documentation describes the implementation of a multi-service application using containerization and Kubernetes, including validation and monitoring evidence.

The implementation covers:
- Container image build and local container validation
- Source control (Git) and repository update
- Kubernetes cluster provisioning (EKS)
- Monitoring verification (Prometheus and Grafana)

---

## Application Endpoints (Local Validation)
- Frontend: `http://localhost:8081`
- Offer page: `http://localhost:8082`
- Backend: `http://localhost:5000`
- Products API: `http://localhost:5000/api/products`

---

## Tools and Components
- Docker (image build, container execution)
- Git and GitHub (version control)
- Kubernetes / EKS (orchestration)
- Prometheus (metrics collection)
- Grafana (metrics visualization)

---

## 1. Repository/Project Directory Validation
A working directory check is performed to confirm the expected files are present before building images.

**Command(s)**
```bash
ls
pwd
```

**Evidence**
![Directory check](../1.check%20the%20dir.jpg.jpeg)

---

## 2. Container Image Build (Docker)

### 2.1 Build Images
Container images are built for the services.

**Command(s)**
```bash
# Example pattern (adjust paths/names based on the project layout)
docker build -t frontend:1.0 ./frontend
docker build -t backend:1.0 ./backend
docker build -t offerpage:1.0 ./offerpage
```

**Evidence**
![Docker build](../2.docker%20build.jpg.jpeg)

### 2.2 Build Success Confirmation
A successful build output is captured.

**Evidence**
![Docker build success](../3.docker%20build%20success.jpg.jpeg)

---

## 3. Local Container Execution and Validation

### 3.1 Containers Running
Containers are started and verified.

**Command(s)**
```bash
docker ps

# Example run commands (ports aligned with the provided endpoints)
docker run -d --name backend -p 5000:5000 backend:1.0
docker run -d --name frontend -p 8081:8081 frontend:1.0
docker run -d --name offerpage -p 8082:8082 offerpage:1.0
```

**Evidence**
![Docker containers running](../4.docker%20container%20runnning.jpg.jpeg)

### 3.2 Frontend Validation
Frontend is verified in the browser.

**Evidence**
![Frontend on server 1](../5.server1%20frontend.jpg.jpeg)  
![Frontend on server 2](../6.server2%20frontend.jpg.jpeg)

### 3.3 Backend Validation
Backend service runtime is validated.

**Evidence**
![Backend running](../7.backend%20running.jpg.jpeg)

### 3.4 API Validation
The products API endpoint is validated.

**Command(s)**
```bash
curl http://localhost:5000/api/products
```

**Evidence**
![API output](../8.api.jpg.jpeg)

---

## 4. Source Control (Git) and Repository Update

### 4.1 Git Repository Status
Repository status is verified prior to staging.

**Command(s)**
```bash
git status
```

**Evidence**
![Git status](../9.git.jpg.jpeg)

### 4.2 Stage Changes
Changes are staged for commit.

**Command(s)**
```bash
git add .
```

**Evidence**
![Git add](../10.git%20add%201.jpg.jpeg)  
![Git add (first)](../11.git%20add%20first.jpg.jpeg)

### 4.3 Commit Changes
Changes are committed with a meaningful message.

**Command(s)**
```bash
git commit -m "Add Docker and Kubernetes deployment assets"
```

**Evidence**
![Commit](../13.commit%20final.jpg.jpeg)

### 4.4 Push to Remote Repository
Changes are pushed to the remote repository.

**Command(s)**
```bash
git push origin main
```

**Evidence**
![Git push](../12.git%20push.jpg.jpeg)

---

## 5. Kubernetes Cluster Provisioning (EKS)

### 5.1 Enable Kubernetes / EKS Setup
Kubernetes is enabled and cluster creation steps are performed.

**Evidence**
![Enable Kubernetes](../14.enable%20kubernetes.jpg.jpeg)

### 5.2 Cluster Configuration
Cluster creation form/configuration is captured.

**Evidence**
![Cluster form](../15.cluster%20form.jpg.jpeg)  
![Cluster form (additional)](../cluster%20form.jpg.jpeg)

### 5.3 Cluster Creation and Availability
Cluster readiness is captured.

**Evidence**
![Cluster created](../16.cluster.jpg.jpeg)  
![Cluster ready](../17.clusterr.jpg.jpeg)

### 5.4 Network Selection / VPC Configuration
Network configuration selection during EKS setup is captured.

**Evidence**
![Specify network in EKS](../specify%20network%20in%20eks.jpg.jpeg)

### 5.5 Kubernetes Validation Commands
Cluster connectivity and workloads are validated using kubectl.

**Command(s)**
```bash
kubectl get nodes
kubectl get pods -A
kubectl get svc -A
```

---

## 6. Monitoring Verification (Prometheus and Grafana)

### 6.1 Prometheus Access and Visibility
Prometheus instance availability is captured.

**Evidence**
![Prometheus](../prometheus.jpg.jpeg)

### 6.2 Prometheus Query Validation
Prometheus successfully queries the application/metrics.

**Evidence**
![Prometheus query success](../prometheus%20successfull%20querried%20the%20api.jpg.jpeg)

### 6.3 Grafana Dashboard Validation
Grafana dashboards display metrics for the environment.

**Evidence**
![Grafana dashboard metrics](../grafana%20dahsboard%20metric.jpg.jpeg)

### 6.4 Monitoring Working Evidence
Additional monitoring evidence is captured.

**Evidence**
![Monitoring work](../monitoring%20work.jpg.jpeg)  
![Monitoring working](../monitoring%20working.jpg.jpeg)

### 6.5 Dashboard Visualizations
Charts/visualizations used for reporting are captured.

**Evidence**
![Histogram monitor](../histogram%20monitor.jpg.jpeg)  
![Bar chart](../bar%20chart%20rep.jpg.jpeg)

---

## Output Summary
- Multi-service application validated locally on the specified ports.
- Changes committed and pushed to GitHub.
- Kubernetes cluster created and validated.
- Monitoring verified with Prometheus and Grafana dashboards.
