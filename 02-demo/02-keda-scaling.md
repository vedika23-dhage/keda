# Configure Keda based scaling

* Now the pods are ready which is running in different nodes
* Let's try to create Keda based scaling

# Example 1

* Memory based scaling

- Scales the cluster based on memory load in pods
- If memory load breaches 50% cluster scales up and scales down if memory load reduces

```
apiVersion: keda.sh/v1alpha1
kind: ScaledObject
metadata:
  name: memory-scaledobject
  namespace: prod
spec:
  scaleTargetRef:
    name: mydeploy
  triggers:
  - type: memory
    metadata:
      type: Utilization
      value: "50"
```

* CPU based scaling

- Scales the cluster based on cpu load in pods
- If cpu load breaches 50% cluster scales up and scales down if cpu load reduces

```
apiVersion: keda.sh/v1alpha1
kind: ScaledObject
metadata:
  name: memory-scaledobject
  namespace: prod
spec:
  scaleTargetRef:
    name: mydeploy
  triggers:
  - type: cpu
    metadata:
      type: Utilization
      value: "50"
```

# How to get results?

```
kubectl get hpa
NAME                           REFERENCE             TARGETS   MINPODS   MAXPODS   REPLICAS   AGE
keda-hpa-memory-scaledobject   Deployment/mydeploy   7%/50%    1         100       1          166m
```

Similarly there are multiple event based scalers are available for different applications

Reference : https://keda.sh/docs/2.6/scalers/