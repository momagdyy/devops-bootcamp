# Lab 16: Kubernetes Init Container for Pre-Deployment Database Setup

## What is an Init Container?
Runs BEFORE the main app container starts.
Does setup work before app starts.
Must complete successfully before app starts.

## In This Lab:
Init container connects to MySQL and creates:
- ivolve database
- ivolve-user with full access

## Init Container Configuration:
- Image: mysql:5.7
- Gets DB credentials from ConfigMap and Secret
- Runs MySQL commands to setup database

## Commands:

```bash
kubectl apply -f deployment.yaml
```

## Verify Init Container Running:

```bash
kubectl get pods -n ivolve -w
```

## Expected Pod Stages:
Init:0/1        -> Init container running
PodInitializing -> Init container done
Running         -> App container started

## Verify Database Created:

```bash
kubectl exec -it mysql-0 -n ivolve -- mysql -u root -proot123
SHOW DATABASES;
SELECT user FROM mysql.user;
```

## Result:
- ivolve database created
- ivolve-user created
- App container started after init