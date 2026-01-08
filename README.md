# connect to client server
   sudo su -

# Install kubectl
 curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
   sudo mv /tmp/eksctl /usr/local/bin
   eksctl version

  aws configure

  aws eks update-kubeconfig --region us-east-1 --name google
   
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
