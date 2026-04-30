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

### Verify:
kubectl describe namespace ivolve

## quota.yaml:
- Limits pods to maximum 2 in ivolve namespace

## Result:
- Namespace ivolve created ✅
- Resource quota applied: max 2 pods ✅

## Key Concepts:
- Namespace = Virtual cluster inside cluster
- Resource Quota = Limit resources per namespace
- Hard limit = Cannot exceed this limit
