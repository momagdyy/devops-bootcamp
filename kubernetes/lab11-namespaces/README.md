# Lab 11: Namespace Management and Resource Quota

## What is a Namespace?
A virtual cluster inside Kubernetes cluster.
Isolates resources between teams/projects.

## What is Resource Quota?
Limits resources that can be used in a namespace.
Prevents one team from using all cluster resources.

## Commands:

### Create namespace:
kubectl create namespace ivolve

### Apply resource quota:
kubectl apply -f quota.yaml
<img width="558" height="56" alt="image" src="https://github.com/user-attachments/assets/23ccf631-5de7-41e7-9a03-eb86b139a9d4" />

### Verify:
kubectl describe namespace ivolve
<img width="639" height="164" alt="image" src="https://github.com/user-attachments/assets/168cafda-aba5-4e57-9d54-c33b396cae2f" />

## quota.yaml:
- Limits pods to maximum 2 in ivolve namespace

## Result:
- Namespace ivolve created ✅
- Resource quota applied: max 2 pods ✅

## Key Concepts:
- Namespace = Virtual cluster inside cluster
- Resource Quota = Limit resources per namespace
- Hard limit = Cannot exceed this limit
