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
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml
kubectl get pods -n ingress-nginx
kubectl get svc -n ingress-nginx
# Install MariaDB
sudo yum update -y
sudo dnf install -y mariadb105
