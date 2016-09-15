###Perform Rolling Update

Verfiy service is available

```
curl $(minikube ip):30080/
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

### Rolling update

```bash
kubectl set image deployment/k8s-hello-world k8s-hello-world=icrosby/tinyping:v2
kubectl rollout status deployment/k8s-hello-world
```
watch status + ping service (curl or browser)
`curl $(minikube ip):[NodePort]/`

----

### Panic and rollback!

```bash
kubectl rollout undo deployment/k8s-hello-world
kubectl rollout status deployment/k8s-hello-world
```

Can check again via curl/browser

