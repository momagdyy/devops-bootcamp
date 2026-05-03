# Lab 17: Pod Resource Management

## What are Resource Requests and Limits?

Requests = Minimum guaranteed resources
           Used for scheduling pods on nodes

Limits = Maximum allowed resources
         Pod cannot exceed this amount

## Resource Configuration:

### Requests:
- cpu: 1 vCPU
- memory: 1Gi

### Limits:
- cpu: 2 vCPUs
- memory: 2Gi

## Commands:

```bash
kubectl apply -f deployment.yaml
```

## Verify Resources:

```bash
kubectl describe pod nodejs-app-xxx -n ivolve
```

## Result:
- Limits: cpu=2, memory=2Gi applied ✅
- Requests: cpu=1, memory=1Gi applied ✅