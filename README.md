# connect to client server
   sudo su -

# Install kubectl
curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl

  aws configure
``` bash
  aws eks update-kubeconfig --region us-east-1 --name google
```   
# for efk stack using ebs volume cluster level need to run add on
Amazon EBS CSI Driver 
need to attach role (aws service -- eks -- EKS - Pod Identity{AmazonEBSCSIDriverPolicy})

# update rds endpoint to backend app.py

# Install Git
yum install git -y
# Install Ingress-Nginx
``` bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml
kubectl get pods -n ingress-nginx
kubectl get svc -n ingress-nginx
```
# Install MariaDB
``` bash
sudo yum update -y
sudo dnf install -y mariadb105
```

## MySQL Database Setup

``` sql
CREATE DATABASE IF NOT EXISTS cloud;
USE cloud;
DROP TABLE IF EXISTS users;
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(100) NOT NULL UNIQUE,
    full_name VARCHAR(150) NOT NULL,
    email VARCHAR(150) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
exit
```

## Install ArgoCD

``` bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
kubectl get svc -n argocd
```
## Create Namespace

``` bash
kubectl create namespace google
```

## Retrieve ArgoCD Password

``` bash
kubectl -n argocd get secret argocd-initial-admin-secret   -o jsonpath="{.data.password}" | base64 -d
```

#to get argocd load balancer url
```bash
kubectl get svc -n argocd
```
