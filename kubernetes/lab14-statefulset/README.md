# Lab 14: StatefulSet with Headless Service

## What is a StatefulSet?
Manages stateful apps like databases.
Pods have stable names (mysql-0, mysql-1).
Good for databases that need stable identity.

## What is a Headless Service?
Service with clusterIP: None.
Returns IP of each pod directly.
Used to connect to specific database pod.

## Files:
- statefulset.yaml: MySQL StatefulSet
- headless-service.yaml: Headless Service

## Key Configurations:
- Toleration: node=worker:NoSchedule
- Secret: MYSQL_ROOT_PASSWORD from mysql-secret
- PVC: app-logs-pvc mounted to /var/lib/mysql
- Replicas: 1

## Commands:
```bash
kubectl apply -f headless-service.yaml
kubectl apply -f statefulset.yaml
```
<img width="619" height="89" alt="image" src="https://github.com/user-attachments/assets/51c25e38-5666-4ac6-a62a-20c31073e1a8" />


## Verify:
```bash
kubectl get statefulset -n ivolve
kubectl get service -n ivolve
kubectl get pods -n ivolve
```
<img width="822" height="219" alt="image" src="https://github.com/user-attachments/assets/05ffde1d-083a-49bd-8b13-e2c8aed32c52" />

## Test Database:
```bash
kubectl exec -it mysql-0 -n ivolve -- mysql -u root -proot123
```
<img width="1067" height="619" alt="image" src="https://github.com/user-attachments/assets/53654234-8eaa-4e8f-b3f3-7b71c238cfce" />

## Result:
- mysql-0 Running ✅
- mysql-service ClusterIP None ✅
- Database accessible ✅
