## Creating and Managing Services

Services provide stable endpoints for Pods based on a set of labels.

In this lab you will create the `k8s-hello-world` service and "expose" the `k8s-hello-world` Pod. You will learn how to:

* Create a service
* Use label selectors to expose a limited set of Pods externally

----

### Tutorial: Create a Service

Explore the k8s-hello-world service configuration file:

```
cat service.yaml
apiVersion: v1
kind: Service
metadata:
  name: k8s-hello-world
spec:
  type: NodePort
  ports:
    - port: 8080
    protocol: TCP
    targetPort: 8080
    nodePort: 30080
  selector:
    app: k8s-hello-world
```
type: NodePort is needed as we don't have a integrated loadbalancer

----

Create the k8s-hello-world service using kubectl:

```
kubectl create -f service.yaml
```

----

### Interact with the k8s-hello-world Service Remotely

```
curl http://$(minikube ip):30080
```
OR
```bash
minikube service k8s-hello-world
```

----

### Explore the k8s-hello-world Service

```
kubectl get services k8s-hello-world
```

```
kubectl describe services k8s-hello-world
```

----

### Using and adding labels to Pods

One way to troubleshoot an issue is to use the `kubectl get pods` command with a label query.

```
kubectl get pods -l "app=k8s-hello-world"
```

With the `kubectl label` command you can add labels like `secure=disabled` to a Pod.

```
kubectl label pods k8s-hello-world 'secure=disabled'
kubectl describe pods k8s-hello-world
```
