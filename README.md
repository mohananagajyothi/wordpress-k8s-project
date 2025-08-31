# WordPress on Kubernetes (KinD)

This project demonstrates how to deploy a WordPress application with a MySQL backend on a **Kubernetes cluster** using **KinD (Kubernetes in Docker)**.  
It uses Kubernetes **Deployments**, **Services**, and **PersistentVolumes** to ensure data persistence.

---

## 🚀 Project Overview
- **Cluster Tool:** KinD (Kubernetes in Docker)
- **App:** WordPress
- **Database:** MySQL
- **Persistence:** PVC for both MySQL and WordPress
- **Access Method:** NodePort / Port-Forward

---

## 📂 Project Structure
 
 wordpress-k8s-project/
│── mysql-deployment.yaml
│── wordpress-deployment.yaml
│── README.md



---

## ⚙️ Setup Instructions

### 1️⃣ Create a KinD Cluster

kind create cluster --name wordpress-cluster

Deploy MySQL

kubectl apply -f mysql-deployment.yaml

Deploy WordPress

kubectl apply -f wordpress-deployment.yaml

Verify Pods

kubectl get pods

Access WordPress

Option A: Port-forward (local access)

kubectl port-forward svc/wordpress 8080:80

👉 Open http://localhost:8080 in browser

Option B: NodePort (direct access)

kubectl get svc wordpress

👉 Access at http://<NodeIP>:30080

🗄️ Persistent Storage

MySQL Data → Stored in PVC (mysql-pv-claim)

WordPress Files → Stored in PVC (wp-pv-claim)

This ensures data is not lost even if pods are restarted.

✅ Verification

MySQL and WordPress pods should show Running:

kubectl get pods


Services should list MySQL (ClusterIP) and WordPress (NodePort):

kubectl get svc




✨ Author

Mohana Naga jyothi Karri (DevOps Engineer)
