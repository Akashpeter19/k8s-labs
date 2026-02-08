# Task 2 – Deploy Nginx on AWS EKS (Fargate)

## Objective
Deploy and run an Nginx application on AWS EKS using Fargate without managing EC2 worker nodes.

---

## Tools Used
- AWS EKS
- AWS Fargate
- eksctl
- kubectl
- Docker (official nginx image)

---

## Steps Performed

### 1. Created EKS Fargate Cluster
An EKS cluster was created using eksctl with Fargate support.

### 2. Verified Cluster Access
Cluster connectivity was verified using:

kubectl get nodes

Note: Fargate manages worker nodes automatically.

### 3. Created Namespace for Nginx
kubectl create namespace nginx

### 4. Created Fargate Profile
eksctl create fargateprofile \
--cluster demo-eks-fargate \
--region us-east-1 \
--name nginx-profile \
--namespace nginx

### 5. Deployed Nginx Application
kubectl apply -f nginx-deployment.yaml

Verified pod status:
kubectl get pods -n nginx

### 6. Exposed Nginx Service
kubectl expose deployment nginx \
-n nginx \
--type=LoadBalancer \
--port=80

### 7. Verified Using Port Forwarding
kubectl port-forward -n nginx deployment/nginx 8080:80

Accessed:
http://localhost:8080

Nginx default page loaded successfully.

---

## Conclusion
Nginx was successfully deployed on AWS EKS using Fargate without managing EC2 instances.

