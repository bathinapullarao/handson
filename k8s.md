# ☸️ Kubernetes Hands-On Task List

This document provides hands-on tasks covering core concepts and widely used features of Kubernetes.

---

## 🚀 Getting Started

### 1. Install Minikube or Connect to a Kubernetes Cluster
- Install Minikube:
  ```bash
  minikube start
  ```

- View cluster info:
  ```bash
  kubectl cluster-info
  ```

---

## 🧱 Pods and Deployments

### 2. Create and Inspect a Pod
- Create a pod using a YAML file:
  ```yaml
  apiVersion: v1
  kind: Pod
  metadata:
    name: nginx-pod
  spec:
    containers:
    - name: nginx
      image: nginx
  ```
  ```bash
  kubectl apply -f pod.yaml
  kubectl get pods
  kubectl describe pod nginx-pod
  ```

### 3. Create a Deployment
- Use:
  ```bash
  kubectl create deployment my-app --image=nginx
  kubectl get deployments
  kubectl scale deployment my-app --replicas=3
  ```

---

## 🔁 Services and Networking

### 4. Create a Service for Your Deployment
- Expose a deployment:
  ```bash
  kubectl expose deployment my-app --port=80 --target-port=80 --type=NodePort
  kubectl get svc
  ```

### 5. Port Forwarding
- Forward a local port:
  ```bash
  kubectl port-forward svc/my-app 8080:80
  ```

---

## 📦 ConfigMaps and Secrets

### 6. Create a ConfigMap
- Use:
  ```bash
  kubectl create configmap app-config --from-literal=APP_ENV=production
  ```

### 7. Create a Secret
- Use:
  ```bash
  kubectl create secret generic db-secret --from-literal=username=admin --from-literal=password=pass
  ```

---

## 🧠 Volumes and Storage

### 8. Use an EmptyDir Volume
- Sample YAML:
  ```yaml
  volumeMounts:
  - name: temp-storage
    mountPath: /app/data
  volumes:
  - name: temp-storage
    emptyDir: {}
  ```

---

## 🔄 Rolling Updates and Rollbacks

### 9. Update the Deployment Image
- Update and rollback:
  ```bash
  kubectl set image deployment/my-app nginx=nginx:1.19
  kubectl rollout status deployment/my-app
  kubectl rollout undo deployment/my-app
  ```

---

## ⏱️ Jobs and CronJobs

### 10. Create a Job
- Use:
  ```yaml
  apiVersion: batch/v1
  kind: Job
  metadata:
    name: hello-job
  spec:
    template:
      spec:
        containers:
        - name: hello
          image: busybox
          command: ["echo", "Hello Kubernetes"]
        restartPolicy: Never
  ```

### 11. Create a CronJob
- Use:
  ```yaml
  apiVersion: batch/v1
  kind: CronJob
  metadata:
    name: hello-cron
  spec:
    schedule: "*/1 * * * *"
    jobTemplate:
      spec:
        template:
          spec:
            containers:
            - name: hello
              image: busybox
              command: ["echo", "Hello from CronJob"]
            restartPolicy: OnFailure
  ```

---

## 🔐 RBAC and Security

### 12. Create a Service Account and RoleBinding
- Use:
  ```bash
  kubectl create serviceaccount viewer
  kubectl create clusterrolebinding viewer-binding --clusterrole=view --serviceaccount=default:viewer
  ```

---

## 📈 Monitoring and Logs

### 13. View Logs
- Use:
  ```bash
  kubectl logs <pod-name>
  kubectl logs -f <pod-name>
  ```

### 14. Install Metrics Server (Minikube)
- Use:
  ```bash
  minikube addons enable metrics-server
  kubectl top nodes
  kubectl top pods
  ```

---

## 🌐 Ingress

### 15. Deploy Ingress Controller and Rules
- Enable Ingress in Minikube:
  ```bash
  minikube addons enable ingress
  ```

- Create an Ingress YAML for routing:
  ```yaml
  apiVersion: networking.k8s.io/v1
  kind: Ingress
  metadata:
    name: example-ingress
  spec:
    rules:
    - host: myapp.local
      http:
        paths:
        - path: /
          pathType: Prefix
          backend:
            service:
              name: my-app
              port:
                number: 80
  ```

---

## 🧪 Advanced

### 16. Taints and Tolerations
- Add taints to a node:
  ```bash
  kubectl taint nodes <node-name> key=value:NoSchedule
  ```

### 17. Node Affinity
- Define scheduling rules in pod spec using `affinity`.

---
