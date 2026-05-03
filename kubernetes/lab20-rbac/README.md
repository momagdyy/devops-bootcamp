# Lab 20: Securing Kubernetes with RBAC and Service Accounts

## What is RBAC?
Role Based Access Control.
Controls who can do what in Kubernetes.
Follows principle of least privilege.

## Key Concepts:
- ServiceAccount = Identity for a pod/app
- Role = Set of permissions
- RoleBinding = Assign role to ServiceAccount

## Files:
- serviceaccount.yaml = jenkins-sa ServiceAccount
- secret.yaml = ServiceAccount token
- role.yaml = pod-reader Role
- rolebinding.yaml = Bind role to ServiceAccount

## Steps:

### 1. Create ServiceAccount:

```bash
kubectl apply -f serviceaccount.yaml
```

### 2. Create Secret for token:

```bash
kubectl apply -f secret.yaml
```

### 3. Create Role:

```bash
kubectl apply -f role.yaml
```

### 4. Create RoleBinding:

```bash
kubectl apply -f rolebinding.yaml
```
<img width="662" height="203" alt="image" src="https://github.com/user-attachments/assets/62ffe379-3866-4812-8280-3b028e6128ae" />

## Verify:

```bash
kubectl get serviceaccount -n ivolve
kubectl get secret -n ivolve
kubectl get role -n ivolve
kubectl get rolebinding -n ivolve
```
<img width="719" height="314" alt="image" src="https://github.com/user-attachments/assets/f4fa4a45-04e5-4c42-aceb-063f8fa7e963" />

## Retrieve Token:

```bash
kubectl describe secret jenkins-sa-token -n ivolve
```

## Validate Permissions:

```bash
kubectl auth can-i list pods --as=system:serviceaccount:ivolve:jenkins-sa -n ivolve
kubectl auth can-i delete pods --as=system:serviceaccount:ivolve:jenkins-sa -n ivolve
```
<img width="801" height="135" alt="image" src="https://github.com/user-attachments/assets/3980766e-a176-4261-bdb1-55b4139fb9c5" />

## Result:
- jenkins-sa created ✅
- pod-reader role created ✅
- RoleBinding created ✅
- Can list pods: yes ✅
- Can delete pods: no ✅

## Key Concepts:
- RBAC = Control who can do what
- ServiceAccount = Identity for apps
- Role = Permissions in a namespace
- RoleBinding = Assign role to account
- Least Privilege = Only minimum permissions
