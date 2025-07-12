# 🚀 Lab: Create and Deploy a Simple Pod in Kubernetes

## 🎯 Objectives

- Define a basic Kubernetes Pod using YAML
- Deploy and verify the Pod using `kubectl`
- Inspect Pod logs and access the running container

---

## 📋 Prerequisites

- Kubernetes cluster (e.g., Minikube, Kind, EKS, etc.)
- `kubectl` CLI installed and configured
- Basic understanding of YAML and Kubernetes concepts

---

## 🛠️ Task 1: Write a Pod YAML Manifest

### 📄 File: `simple-pod.yaml`

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
  labels:
    app: nginx
spec:
  containers:
  - name: nginx-container
    image: nginx:latest
    ports:
    - containerPort: 80
```

### 🧠 Explanation

| Key        | Description                                     |
|------------|-------------------------------------------------|
| apiVersion | Defines the Kubernetes API version used         |
| kind       | Type of resource (here, it's a Pod)             |
| metadata   | Includes name and labels for identification     |
| spec       | Defines container details (image, port, etc.)   |

✅ **Expected:** A valid YAML file defining an Nginx-based Pod.

---

## 🚀 Task 2: Deploy the Pod

### 🔹 Subtask 2.1: Apply the YAML File

```bash
kubectl apply -f simple-pod.yaml
```

✅ Expected Output:
```
pod/nginx-pod created
```

---

### 🔹 Subtask 2.2: Verify Pod Deployment

```bash
kubectl get pods
```

✅ Expected Output:

```
NAME        READY   STATUS    RESTARTS   AGE
nginx-pod   1/1     Running   0          10s
```

---

### 🛠️ Troubleshooting Tips

| Issue             | Command                                 |
|------------------|------------------------------------------|
| Pod stuck Pending | `kubectl describe pod nginx-pod`        |
| Pod crashing      | `kubectl logs nginx-pod`                |

---

## 🔍 Task 3: Inspect Pod Status and Logs

### 🔹 Subtask 3.1: Describe the Pod

```bash
kubectl describe pod nginx-pod
```

📋 View:
- Events
- IP address
- Container details

---

### 🔹 Subtask 3.2: View Pod Logs

```bash
kubectl logs nginx-pod
```

📋 You should see Nginx access and error logs.

---

### 🔹 Subtask 3.3: Access the Pod via Port Forwarding (Optional)

```bash
kubectl port-forward nginx-pod 8080:80
```

Then visit in your browser:  
👉 [http://localhost:8080](http://localhost:8080)

✅ Expected: Nginx Welcome Page

---

## 🧹 Cleanup

```bash
kubectl delete pod nginx-pod
```

---

## 👨‍💻 Author

**Abdullha Saleem** – Kubernetes | DevOps | YAML | Containers  
📫 *Connect with me on GitHub or LinkedIn for more labs.*
