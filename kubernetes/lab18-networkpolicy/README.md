# Lab 18: Control Pod-to-Pod Traffic via Network Policy

## What is a Network Policy?
Firewall rules for pods in Kubernetes.
Controls which pods can talk to which pods.
By default all pods can communicate freely.

## In This Lab:
Allow ONLY nodejs-app pods to talk to MySQL on port 3306.
Block all other traffic to MySQL.

## Network Policy Specifications:
- Name: allow-app-to-mysql
- Pod Selector: Targets pods with label app=mysql
- Policy Type: Ingress only
- Ingress Rule: Allow traffic from app=nodejs-app on port 3306

## Commands:

```bash
kubectl apply -f networkpolicy.yaml
```

## Verify:

```bash
kubectl get networkpolicy -n ivolve
kubectl describe networkpolicy allow-app-to-mysql -n ivolve
```

## Result:
- NetworkPolicy created ✅
- Only nodejs-app can reach MySQL on port 3306 ✅
- All other traffic to MySQL blocked ✅

## Key Concepts:
- Network Policy = Firewall rules for pods
- podSelector = Which pods this policy applies to
- Ingress = Incoming traffic rules
- Egress = Outgoing traffic rules
  <img width="830" height="322" alt="image" src="https://github.com/user-attachments/assets/de7f8d1d-61f4-4b68-a3ed-1869a93420f8" />
