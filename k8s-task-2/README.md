# Task 2 – Deploy Nginx on AWS EKS Fargate

This folder contains all files related to Task 2, where an Nginx application was deployed on an AWS EKS Fargate cluster.

## Folder Structure

k8s-task-2/
├── README.md
├── k8s-task-2.txt # Original task explanation
├── nginx-deployment.yaml # Kubernetes deployment manifest for Nginx
└── screenshots-task2/ # Screenshots showing steps and results

## Task Overview

1. Created a **namespace** and **Fargate profile** in AWS EKS for Nginx.
2. Created an **Nginx deployment** using `nginx-deployment.yaml`.
3. Exposed the deployment via a **LoadBalancer service**.
4. Verified the deployment using **port-forward** and **LoadBalancer URL**.
5. Screenshots in `screenshots-task2/` demonstrate each step visually.

## Key Commands Used

```bash
# Verify Fargate nodes
kubectl get nodes

# Create namespace
kubectl create namespace nginx

# Apply deployment
kubectl apply -f nginx-deployment.yaml -n nginx

# Expose service
kubectl expose deployment nginx -n nginx --type=LoadBalancer --port=80

# Port-forward for local testing
kubectl port-forward -n nginx deployment/nginx 8080:80

