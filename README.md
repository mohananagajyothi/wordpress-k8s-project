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


```

wordpress-k8s-project/
│── kind-config.yaml
│── mysql-deployment.yaml
│── wordpress-deployment.yaml
│── README.md

````

---

## ⚙️ Setup Instructions

### 1️⃣ Create a KinD Cluster
```bash
kind create cluster --name wordpress-cluster --config kind-config.yaml
````

### 2️⃣ Deploy MySQL

```bash
kubectl apply -f mysql-deployment.yaml
```

### 3️⃣ Deploy WordPress

```bash
kubectl apply -f wordpress-deployment.yaml
```

### 4️⃣ Verify Pods

```bash
kubectl get pods
```

### 5️⃣ Access WordPress

**Option A: Port-forward (local access)**

```bash
kubectl port-forward svc/wordpress 8080:80
```

👉 Open [http://localhost:8080](http://localhost:8080) in your browser

**Option B: NodePort (direct access)**

```bash
kubectl get svc wordpress
```

👉 Access at:

```
http://<NodeIP>:30080
```

---

## 🗄️ Persistent Storage

* **MySQL Data** → Stored in PVC (`mysql-pv-claim`)
* **WordPress Files** → Stored in PVC (`wp-pv-claim`)

This ensures data is not lost even if pods are restarted.

---

## ✅ Verification

Check running pods:

```bash
kubectl get pods
```

Check services:

```bash
kubectl get svc
```

You should see MySQL (ClusterIP) and WordPress (NodePort).

---

## ✨ Author

**Mohana Naga Jyothi Karri** (DevOps Engineer)

