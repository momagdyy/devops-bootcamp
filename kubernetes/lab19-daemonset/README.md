# Lab 19: Node-Wide Pod Management with DaemonSet

## What is a DaemonSet?
Runs ONE copy of a pod on EVERY node automatically.
New node added = pod added automatically.
Node removed = pod removed automatically.

## What is Prometheus Node Exporter?
Collects metrics from each node:
- CPU usage
- Memory usage
- Disk usage
- Network stats
Exposes metrics on port 9100/metrics

## Steps:

### 1. Create monitoring namespace:

```bash
kubectl create namespace monitoring
```
<img width="570" height="51" alt="image" src="https://github.com/user-attachments/assets/d353e4a1-e7e5-44ce-81e2-a4bc02207b05" />

### 2. Apply DaemonSet:

```bash
kubectl apply -f daemonset.yaml
```
<img width="550" height="48" alt="image" src="https://github.com/user-attachments/assets/05a204f5-4d41-4a6c-8e8b-c7566d3243a7" />

### 3. Verify pods on each node:

```bash
kubectl get daemonset -n monitoring
kubectl get pods -n monitoring
```
<img width="838" height="157" alt="image" src="https://github.com/user-attachments/assets/8075f728-4da3-472b-98ac-079c6a24d052" />

### 4. Verify metrics:

```bash
kubectl port-forward daemonset/node-exporter 9100:9100 -n monitoring
```
<img width="913" height="114" alt="image" src="https://github.com/user-attachments/assets/842e381f-7cfd-4a74-929a-a4bd00e616cb" />

Then open: http://localhost:9100/metrics
<img width="1919" height="967" alt="image" src="https://github.com/user-attachments/assets/74c8872e-3eff-49f9-a8bd-e2c9481dc9b7" />

## Result:
- node-exporter running on minikube ✅
- node-exporter running on minikube-m02 ✅
- Metrics exposed on port 9100 ✅
- DaemonSet tolerates all taints ✅

## Key Concepts:
- DaemonSet = One pod per node
- Tolerations operator Exists = Tolerates ALL taints
- Node Exporter = Collects node metrics
- Port 9100 = Metrics endpoint
