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
-kubectl apply -f headless-service.yaml
-kubectl apply -f statefulset.yaml

## Verify:
kubectl get statefulset -n ivolve
kubectl get service -n ivolve
kubectl get pods -n ivolve

## Test Database:
kubectl exec -it mysql-0 -n ivolve -- mysql -u root -proot123

## Result:
- mysql-0 Running ✅
- mysql-service ClusterIP None ✅
- Database accessible ✅
