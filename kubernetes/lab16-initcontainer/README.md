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
<img width="749" height="96" alt="image" src="https://github.com/user-attachments/assets/8e1945f7-9c22-49d8-9eb5-3bcb736c9857" />

## Expected Pod Stages:
Init:0/1        -> Init container running
PodInitializing -> Init container done
Running         -> App container started
<img width="719" height="52" alt="image" src="https://github.com/user-attachments/assets/f761cc43-5beb-4055-853d-384664c90e8b" />

## Verify Database Created:

```bash
kubectl exec -it mysql-0 -n ivolve -- mysql -u root -proot123
SHOW DATABASES;
SELECT user FROM mysql.user;
```
<img width="1225" height="431" alt="image" src="https://github.com/user-attachments/assets/0373217d-5da5-48ab-9dae-398a1b0ae6c8" />

## Result:
- ivolve database created
- ivolve-user created
- App container started after init
