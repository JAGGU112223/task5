🚀 Kubernetes Nginx Deployment
📌 Project Overview
This project demonstrates deploying an Nginx web server on a Kubernetes cluster using kubectl.
We create a Deployment, expose it as a NodePort Service, and access it externally via the server's public IP.

🧰 Tools & Technologies Used
Docker – Containerization platform
kubectl – Kubernetes command-line tool
Minikube / Kubernetes cluster – Container orchestration platform
AWS EC2 – Cloud instance hosting the Kubernetes cluster
📂 Files in This Repository
deployment.yaml – Kubernetes manifest for Nginx deployment.
service.yaml – Kubernetes manifest for exposing Nginx service via NodePort.
screenshots/ – Screenshots showing commands and outputs.
README.md – Project documentation (this file).
🛠 Steps Performed
1️⃣ Install Prerequisites
Installed the following on the EC2 instance: 'bash sudo apt update sudo apt install -y docker.io sudo apt install -y apt-transport-https ca-certificates curl sudo snap install kubectl --classic Also installed minikube to create a local Kubernetes cluster.

2️⃣ Start Kubernetes Cluster bash Copy Edit minikube start --driver=docker kubectl get nodes Verified that the control-plane node is ready.

3️⃣ Create Deployment Used kubectl to create a deployment running Nginx:

bash Copy Edit kubectl create deployment hello-deployment --image=nginx kubectl get deployments 4️⃣ Expose Deployment via NodePort Created a service to expose the Nginx deployment:

bash Copy Edit kubectl expose deployment hello-deployment --type=NodePort --port=80 kubectl get svc Example output:

pgsql Copy Edit NAME TYPE CLUSTER-IP EXTERNAL-IP PORT(S) AGE hello-deployment NodePort 10.96.225.0 80:31074/TCP 1m kubernetes ClusterIP 10.96.0.1 443/TCP 83d 5️⃣ Access Application Externally Checked the EC2 public IP:

bash Copy Edit curl ifconfig.me Example output:

Copy Edit 13.49.102.108 Opened AWS Security Group and allowed NodePort range (30000–32767) in inbound rules.

Accessed in browser:

cpp Copy Edit http://13.49.102.108:31074
