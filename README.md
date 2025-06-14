# 🐬 MySQL StatefulSet with Headless Service on Kubernetes

This project is a real-world implementation of a **MySQL StatefulSet with a Headless Service** in Kubernetes — inspired by [Abhishek Veramala’s YouTube tutorial](https://www.youtube.com/watch?v=NOjCunqu3VA). The purpose of this setup is to demonstrate stable pod DNS resolution and scalable database deployment using Kubernetes-native constructs.

---

## 📌 What You’ll Learn

✅ How to deploy MySQL using a **StatefulSet**  
✅ How to create a **Headless Service** (`clusterIP: None`)  
✅ How Kubernetes assigns **stable DNS** to StatefulSet pods  
✅ How to test pod-level DNS resolution via `nslookup`  
✅ How to structure a production-ready database YAML deployment

---

## 📁 Project Structure

k8s-headless-mysql/
├── mysql-headless-service.yaml # Headless service definition
├── mysql-statefulset.yaml # MySQL StatefulSet (3 replicas)
├── test-dns-resolution.md # DNS verification steps
└── screenshots/ # Optional CLI result screenshots
├── pods.png
├── svc.png
└── nslookup.png


---

## ⚙️ Prerequisites

- A running Kubernetes cluster (e.g., Minikube, Kind, EKS, GKE, etc.)
- `kubectl` configured and connected to your cluster
- Namespace `db` created (or change YAML to use `default`)


## 📄 Files

| File                        | Description                          |
|-----------------------------|--------------------------------------|
| `mysql-headless-service.yaml` | Defines the headless service        |
| `mysql-statefulset.yaml`      | Deploys 3-replica MySQL StatefulSet |
| `test-dns-resolution.md`      | Commands to verify DNS lookup       |
| `screenshots/`                | Terminal outputs and results        |

## 🔍 DNS Test Command

```bash
kubectl run -n db -it --rm --restart=Never --image=busybox dns-test \
  -- nslookup mysql-statefulset-0.my-db-headless-service.db.svc.cluster.local
