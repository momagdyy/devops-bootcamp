# Lab 15: Node.js Application Deployment with ClusterIP Service

## What is a Deployment?
Manages multiple copies (replicas) of your app.
Automatically restarts pods if they crash.

## What is ClusterIP Service?
Internal service accessible only inside cluster.
Load balances traffic between pods.
Has permanent IP unlike pods.

## Files:
- deployment.yaml: NodeJS app deployment
- clusterip-service.yaml: ClusterIP Service

## Key Configurations:
- Replicas: 2 (1 running due to taint)
- Image: megzz22/ivolve-app:latest
- Toleration: node=worker:NoSchedule
- ConfigMap: DB_HOST, DB_USER
- Secret: DB_PASSWORD
- PVC: app-logs-pvc mounted to /app/logs

## Commands:
kubectl apply -f deployment.yaml
kubectl apply -f clusterip-service.yaml

## Verify:
kubectl get deployment -n ivolve
kubectl get pods -n ivolve
kubectl get service -n ivolve

## Result:
- nodejs-app: 1/2 Ready (1 pod due to taint) ✅
- nodejs-service ClusterIP: 10.107.39.180 ✅

## Key Concepts:
- Deployment = Manages pod replicas
- ClusterIP = Internal load balancer
- Never use Pod IP directly
- Service IP is permanent unlike Pod IP
