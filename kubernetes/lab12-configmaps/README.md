# Lab 12: ConfigMaps and Secrets

## What is a ConfigMap?
Stores non-sensitive configuration outside the app.
No need to rebuild image when config changes.

## What is a Secret?
Stores sensitive data like passwords.
Data is base64 encoded for security.

## Files:

### configmap.yaml:
- DB_HOST: MySQL service hostname
- DB_USER: Database user

### secret.yaml:
- DB_PASSWORD: base64 encoded password
- MYSQL_ROOT_PASSWORD: base64 encoded root password

## Commands:
kubectl apply -f configmap.yaml

kubectl apply -f secret.yaml
<img width="632" height="89" alt="image" src="https://github.com/user-attachments/assets/0c5c6aaa-b622-4846-ba5c-0059a8e1bb58" />


## Verify:
kubectl get configmap -n ivolve

kubectl get secret -n ivolve

kubectl describe configmap mysql-config -n ivolve

kubectl describe secret mysql-secret -n ivolve
<img width="831" height="507" alt="image" src="https://github.com/user-attachments/assets/97de41d3-3d24-4fed-8ce0-0863e116294f" />

## Key Concepts:
- ConfigMap = Non-sensitive config storage
- Secret = Sensitive data storage
- base64 = Encoding method for secret values
- Opaque = Default secret type for passwords/tokens
