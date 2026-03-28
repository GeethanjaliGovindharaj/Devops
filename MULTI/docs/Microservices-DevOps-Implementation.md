# Microservices DevOps Implementation

## Overview
This documentation describes the implementation of a multi-service application using containerization and Kubernetes, including validation and monitoring evidence.

The implementation covers:
- Compute provisioning evidence (EC2)
- Continuous integration evidence (Jenkins)
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
- AWS EC2 (compute instance provisioning)
- Jenkins (CI orchestration)
- Docker (image build, container execution)
- Git and GitHub (version control)
- Kubernetes / EKS (orchestration)
- Prometheus (metrics collection)
- Grafana (metrics visualization)

---

## 1. EC2 Provisioning Evidence
This section captures the provisioning steps and security configuration associated with compute setup.

### 1.1 Key Pair and Network Settings
**Evidence**  
![EC2 key pair and network settings](../ec2%20key%20pair%20and%20network%20settings.jpg.jpeg)

### 1.2 Security Group Configuration
**Evidence**  
![EC2 add security group](../ec2%20add%20security%20group.jpg.jpeg)

### 1.3 Instance Creation
**Evidence**  
![EC2 instance creation](../ec2%20instance%20creation.jpg.jpeg)

### 1.4 Docker Installation on EC2
After launching the EC2 instance, Docker is installed and verified so that containers can be built/run on the server.

**Evidence**  
![EC2 docker installation](../ec2%20docker%20installation.jpg.jpeg)  
![EC2 docker installation final](../ec2%20docker%20installation%20final.jpg.jpeg)

### 1.5 EC2 Creation Summary
**Evidence**  
![EC2 creation](../ec2%20creation.jpg.jpeg)

---

## 2. Jenkins Continuous Integration Evidence
This section captures Jenkins configuration evidence for repository integration and main branch pull activity.

### 2.1 Jenkins Freestyle Job and Git Configuration
**Evidence**  
![Jenkins freestyle git](../jenkins%20freestyle%20git.jpg.jpeg)

### 2.2 Jenkins Main Branch Pull
**Evidence**  
![Jenkins main branch pull](../jenkins%20main%20branch%20pull.jpg.jpeg)

---

## 3. Repository/Project Directory Validation
A working directory check is performed to confirm the expected files are present before building images.

**Command(s)**
```bash
ls
pwd
```

**Evidence**  
![Directory check](../1.check%20the%20dir.jpg.jpeg)

---

## 4. Container Image Build (Docker)

### 4.1 Build Images
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

### 4.2 Build Success Confirmation
A successful build output is captured.

**Evidence**  
![Docker build success](../3.docker%20build%20success.jpg.jpeg)

---

## 5. Local Container Execution and Validation

### 5.1 Containers Running
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

### 5.2 Frontend Validation
**Evidence**  
![Frontend on server 1](../5.server1%20frontend.jpg.jpeg)  
![Frontend on server 2](../6.server2%20frontend.jpg.jpeg)

### 5.3 Backend Validation
**Evidence**  
![Backend running](../7.backend%20running.jpg.jpeg)

### 5.4 API Validation
The products API endpoint is validated.

**Command(s)**
```bash
curl http://localhost:5000/api/products
```

**Evidence**  
![API output](../8.api.jpg.jpeg)

---

## 6. Source Control (Git) and Repository Update

### 6.1 Git Repository Status
**Command(s)**
```bash
git status
```

**Evidence**  
![Git status](../9.git.jpg.jpeg)

### 6.2 Stage Changes
**Command(s)**
```bash
git add .
```

**Evidence**  
![Git add](../10.git%20add%201.jpg.jpeg)  
![Git add (first)](../11.git%20add%20first.jpg.jpeg)

### 6.3 Commit Changes
**Command(s)**
```bash
git commit -m "Add Docker and Kubernetes deployment assets"
```

**Evidence**  
![Commit](../13.commit%20final.jpg.jpeg)

### 6.4 Push to Remote Repository
**Command(s)**
```bash
git push origin main
```

**Evidence**  
![Git push](../12.git%20push.jpg.jpeg)

---

## 7. Kubernetes Cluster Provisioning (EKS)

### 7.1 Enable Kubernetes / EKS Setup
**Evidence**  
![Enable Kubernetes](../14.enable%20kubernetes.jpg.jpeg)

### 7.2 Cluster Configuration
**Evidence**  
![Cluster form](../15.cluster%20form.jpg.jpeg)  
![Cluster form (additional)](../cluster%20form.jpg.jpeg)

### 7.3 Cluster Creation and Availability
**Evidence**  
![Cluster created](../16.cluster.jpg.jpeg)  
![Cluster ready](../17.clusterr.jpg.jpeg)

### 7.4 Network Selection / VPC Configuration
**Evidence**  
![Specify network in EKS](../specify%20network%20in%20eks.jpg.jpeg)

### 7.5 Kubernetes Validation Commands
Cluster connectivity and workloads are validated using kubectl.

**Command(s)**
```bash
kubectl get nodes
kubectl get pods -A
kubectl get svc -A
```

---

## 8. Monitoring Verification (Prometheus and Grafana)

### 8.1 Prometheus Access and Visibility
**Evidence**  
![Prometheus](../prometheus.jpg.jpeg)

### 8.2 Prometheus Query Validation
**Evidence**  
![Prometheus query success](../prometheus%20successfull%20querried%20the%20api.jpg.jpeg)

### 8.3 Grafana Dashboard Validation
**Evidence**  
![Grafana dashboard metrics](../grafana%20dahsboard%20metric.jpg.jpeg)

### 8.4 Monitoring Working Evidence
**Evidence**  
![Monitoring work](../monitoring%20work.jpg.jpeg)  
![Monitoring working](../monitoring%20working.jpg.jpeg)

### 8.5 Dashboard Visualizations
**Evidence**  
![Histogram monitor](../histogram%20monitor.jpg.jpeg)  
![Bar chart](../bar%20chart%20rep.jpg.jpeg)

---

## Output Summary
- EC2 provisioning + Docker installation evidence captured.
- Jenkins CI evidence captured.
- Multi-service application validated locally on the specified ports.
- Changes committed and pushed to GitHub.
- Kubernetes cluster created and validated.
- Monitoring verified with Prometheus and Grafana dashboards.
