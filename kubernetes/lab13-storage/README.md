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
<img width="785" height="140" alt="image" src="https://github.com/user-attachments/assets/42ae2e7d-2bc7-4cc8-88c3-883e8f4de6ab" />

### 2. Create PV:
kubectl apply -f pv.yaml
<img width="523" height="55" alt="image" src="https://github.com/user-attachments/assets/df9e51b5-b0af-4266-b6f5-105e80d84794" />

### 3. Create PVC:
kubectl apply -f pvc.yaml
<img width="482" height="52" alt="image" src="https://github.com/user-attachments/assets/f8c2950d-7a7a-4132-9cb7-4e48fdf1f132" />

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
<img width="963" height="211" alt="image" src="https://github.com/user-attachments/assets/21fb5d23-9bec-4dc4-b2ac-9128690bde86" />

## Key Concepts:
- PV = Actual storage (hard drive)
- PVC = Request for storage (ticket)
- hostPath = Store on node filesystem
- Retain = Keep data after PVC deleted
- ReadWriteMany = Multiple pods can read/write
- StorageClass = Must match between PV and PVC
