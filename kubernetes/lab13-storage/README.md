# Lab 13: Persistent Storage Setup for Application Logging

## What is Persistent Storage?
Stores data outside containers so it survives restarts.

## What is PV?
PersistentVolume = Actual storage on node filesystem.
Like a hard drive that exists independently.

## What is PVC?
PersistentVolumeClaim = Request for storage.
App uses PVC to access PV.

## Steps:

### 1. Create directory on worker node:
minikube ssh -n minikube-m02
sudo mkdir -p /mnt/app-logs
sudo chmod 777 /mnt/app-logs

### 2. Create PV:
kubectl apply -f pv.yaml

### 3. Create PVC:
kubectl apply -f pvc.yaml

## PV Specifications:
- Size: 1Gi
- Storage type: hostPath
- Path: /mnt/app-logs
- Access mode: ReadWriteMany
- Reclaim policy: Retain
- StorageClass: manual

## PVC Specifications:
- Size: 1Gi
- Access mode: ReadWriteMany
- StorageClass: manual

## Result:
- app-logs-pv  → Bound ✅
- app-logs-pvc → Bound to app-logs-pv ✅

## Key Concepts:
- PV = Actual storage (hard drive)
- PVC = Request for storage (ticket)
- hostPath = Store on node filesystem
- Retain = Keep data after PVC deleted
- ReadWriteMany = Multiple pods can read/write
- StorageClass = Must match between PV and PVC
