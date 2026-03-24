# Title:-

Kubernetes-Based Microservices Deployment with Ingress, RBAC, and Persistent Storage

# Project overview:- 

This project demonstrates the deployment of a multi-tier application on Kubernetes, including frontend and backend services, with proper networking, storage, and security configurations.
The setup follows a production-like architecture using Kubernetes resources such as Deployments, Services, Ingress, Persistent Volumes, ConfigMaps, Secrets, and RBAC.
In networking mostly tried to cover many networking mainly Node port, Cluster IP, Ingress

# Architecture:- 

- Frontend and Backend deployed as separate services
- Internal communication via ClusterIP
- External access via Ingress
- Persistent storage using PV, PVC, and StorageClass
- Secure configuration using Secrets and RBAC
![Kubernetes Architecture](https://github.com/user-attachments/assets/c5d7398e-b60b-4814-a4e8-eedd75bb0326)

# Tech stack:-

- Kubernetes
- Docker
- YAML
- NGINX (Ingress / FE if used)
- Docker build Image (for BE is used)

# Project Structure:-

Lab3
├──
 project-1-multi-tier-app
 
    ├── storageclass.yml
   
    ├── pv.yml
   
    ├── pvc.yml
   
    ├── deployment.yml
   
    ├── service.yml
   
    ├── clusterip.yml
   
    ├── ingress.yml
   
    ├── configmap.yml
   
    ├── secret.yml
   
    ├── RBAC.yml
   
    ├── fe-deployment.yml
   
    ├── fe-service.yml
   
    ├── be-deployment.yml
   
    ├── be-service.yml
   
# Deployment Steps:-

# Step 1: Create namespace 
kubectl create namespace iot-nsp

# Step 2: Apply storage resources
kubectl apply -f storageclass.yml
kubectl apply -f pv.yml
kubectl apply -f pvc.yml

# Step 3: Apply config and secrets
kubectl apply -f configmap.yml
kubectl apply -f secret.yml

# Step 4: Apply RBAC
kubectl apply -f RBAC.yml

# Step 5: Deploy backend and frontend
kubectl apply -f be-deployment.yml
kubectl apply -f be-service.yml
kubectl apply -f fe-deployment.yml
kubectl apply -f fe-service.yml

# Step 6: Apply ingress
kubectl apply -f ingress.yml


# Access application:-

- Access application via URL:
  http://<your-domain-or-ip> or http://localhost

- Or using NodePort:
  http://<node-ip>:<port> or http://localhost:30080

- To verify clusterip configuration
  on terminal hit command as: kubectl exec -it <deployment name> -n <namespace> -- curl http://<clusterip.yml metadata name>
  
- To verify for ingress via URL
  http://localhost/  (will get nginx welcome page as FE )
  http://localhost/api (will get docker container running output as BE)
  
# Security features:-

- Secrets used for sensitive data
- RBAC implemented for access control
- Namespace isolation (iot-nsp)


# Storage:-

- Persistent Volume (PV) for storage
- Persistent Volume Claim (PVC) for access
- StorageClass for dynamic provisioning

# Key Learning:-

- Kubernetes networking (ClusterIP, Ingress)
- Storage management (PV, PVC, StorageClass)
- Secure configurations using Secrets and RBAC
- Multi-tier application deployment

# Future improvements:-

- Add CI/CD pipeline (GitHub Actions / Jenkins)
- Implement Horizontal Pod Autoscaler (HPA)
- Use Helm charts for deployment
- Add monitoring (Prometheus + Grafana)

# Author:

## Rohit Shinde


