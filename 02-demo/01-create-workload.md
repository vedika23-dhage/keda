# Let see how to create simple workload in kubernetes cluster

## Expected prior knowledge

* Understading about kubernetes objects such as (PODs, Replicas and Deployment)

## Let's see what are these objects in short

    - What is PODs?
    * Pods are the smallest, objects in Kubernetes
    * Pods can contain one or more containers

    - What is Replicas?
    * A ReplicaSet (RS) is a Kubernetes object that ensures identical pods run in different node to enable high availability
  
    - What is Deployment?
    * Deployment wrap up Pods & ReplicaSets into a nice package
    * Deployment is a higher abstraction that manages one or more replicaset
    * Also deployment helps to rollout newer version of application to all pods

## Workload creation manifest file

* Lets divide this code into 3 blocks

- block 1 : 
    Creats high level absractions such as deployment and replicas object
    Its going to created 1 pods since we mentioned replicas as 1

- block 2 : 
    Creates pods and attach it with object deployment

- block 3 : 
    Creates containers inside pod
    We can use any image to create containers
    Exposing port 80
    Setting up memory limits for container usage

```
# block 1
apiVersion: apps/v1
kind: Deployment
metadata:
  name: mydeploy
  labels:
    name: prod-deploy
spec:
  replicas: 1
  selector:
    matchLabels:
      app: apache
      env: prod

# block 2
  template:
    metadata:
      name: apache-pod
      labels:
        app: apache
        env: prod

# block 3
    spec:
      containers:
      - name: apache
        image: httpd:2
        ports:
        - containerPort: 80
        resources:
          limits:
            memory: "200Mi"
          requests:
            memory: "100Mi"
```

## Post apply checks

* Note: We can use `kubectl` command line utility to retrive objects created

`kubectl get deployment` returns deployment object

```
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
mydeploy   1/1     1            1           54m
```

`kubectl get replicaset` returns replicasets 

```
NAME                  DESIRED   CURRENT   READY   AGE
mydeploy-544d7cddcf   1         1         1       62m
```

`kubectl get pods` returns pod results

```
NAME                        READY   STATUS                       RESTARTS      AGE
mydeploy-544d7cddcf-vr7qq   1/1     Running                      0             63m
```

* Describe commands to get full details of created objects

`kubectl decribe deploy <object-name>`

`kubectl decribe replicaset <object-name>`

`kubectl describe pods`
