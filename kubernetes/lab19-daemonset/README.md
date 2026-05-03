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

### 2. Apply DaemonSet:

```bash
kubectl apply -f daemonset.yaml
```

### 3. Verify pods on each node:

```bash
kubectl get daemonset -n monitoring
kubectl get pods -n monitoring
```

### 4. Verify metrics:

```bash
kubectl port-forward daemonset/node-exporter 9100:9100 -n monitoring
```

Then open: http://localhost:9100/metrics

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