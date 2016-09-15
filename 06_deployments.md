###Perform Rolling Update

Remove old pod

```
kubectl delete pods k8s-hello-world
```

----

### Create new deployment

`cat deployment.yaml`

Notice "rollingUpdate" strategy and "replicas: 5"

----

### Create and view status

```
kubectl create -f deployment.yaml
kubectl describe deployments k8s-hello-world
```

Watch new pods created: `kubectl get pods`

----

### Call service

```
curl $(minikube ip):30080/
```

or

```
minikube service k8s-hello-world
```

----

### Rolling update

```bash
kubectl set image deployment/k8s-hello-world k8s-hello-world=icrosby/tinyping:v2
kubectl rollout status deployment/k8s-hello-world
```
watch status + ping service (curl or browser)
`curl $(minikube ip):30080//`

----

### Panic and rollback!

```bash
kubectl rollout undo deployment/k8s-hello-world
kubectl rollout status deployment/k8s-hello-world
```

Can check again via curl/browser

