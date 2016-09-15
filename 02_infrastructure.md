## Prepare the infrastructure
Clone the repo [https://github.com/ContainerSolutions/kubernetes-workshop](https://github.com/ContainerSolutions/kubernetes-workshop)

Minikube isn't shipped with weave installed so we need to install it.

----

### Installation of kubectl and minikube
kubectl
```bash
# linux/amd64
curl -Lo kubectl http://storage.googleapis.com/kubernetes-release/release/v1.3.0/bin/linux/amd64/kubectl && chmod +x kubectl && sudo mv kubectl /usr/local/bin/
# linux/386
curl -Lo kubectl http://storage.googleapis.com/kubernetes-release/release/v1.3.0/bin/linux/386/kubectl && chmod +x kubectl && sudo mv kubectl /usr/local/bin/
# linux/arm
curl -Lo kubectl http://storage.googleapis.com/kubernetes-release/release/v1.3.0/bin/linux/arm/kubectl && chmod +x kubectl && sudo mv kubectl /usr/local/bin/
# linux/arm64
curl -Lo kubectl http://storage.googleapis.com/kubernetes-release/release/v1.3.0/bin/linux/arm64/kubectl && chmod +x kubectl && sudo mv kubectl /usr/local/bin/
#linux/ppc64le
curl -Lo kubectl http://storage.googleapis.com/kubernetes-release/release/v1.3.0/bin/linux/ppc64le/kubectl && chmod +x kubectl && sudo mv kubectl /usr/local/bin/
# OS X/amd64 
curl -Lo kubectl http://storage.googleapis.com/kubernetes-release/release/v1.3.0/bin/darwin/amd64/kubectl && chmod +x kubectl && sudo mv kubectl /usr/local/bin/
# OS X/386 
curl -Lo kubectl http://storage.googleapis.com/kubernetes-release/release/v1.3.0/bin/darwin/386/kubectl && chmod +x kubectl && sudo mv kubectl /usr/local/bin/

# The generic download path is: 
https://storage.googleapis.com/kubernetes-release/release/${K8S_VERSION}/bin/${GOOS}/${GOARCH}/${K8S_BINARY}
```
minikube
```bash
# OSX

curl -Lo minikube https://storage.googleapis.com/minikube/releases/v0.8.0/minikube-darwin-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/

# Feel free to leave off the sudo mv minikube /usr/local/bin if you would like to add minikube to your path manually.

# Linux

curl -Lo minikube https://storage.googleapis.com/minikube/releases/v0.8.0/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/
```

----

### Start minikube  
`minikube start`

`kubectl cluster-info`

ssh into the VM

```bash
minikube ssh
sudo wget -O /usr/local/bin/scope https://git.io/scope
sudo chmod a+x /usr/local/bin/scope
sudo scope launch
exit
```
This will download and start weave scope

----

### Lauch the application
`kubectl create -f wholeWeaveDemo.yaml`

----

### Access the front-end
`minikube service front-end`

This will open the front-end with the default browser
### Access weave Scope
`open http://$(minikube ip):4040` 