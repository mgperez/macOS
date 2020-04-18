# Minikube

In order to run Kubernetes clusters locally, there are different alternatives. One is to use the Kubernetes functionality integrated in Docker Desktop. The alternative that I’ve chosen is Minikube which runs a single-node Kubernetes cluster inside a VM on your development machine.

https://gist.github.com/kevin-smets/b91a34cea662d0c523968472a81788f7



- [Setup Local Kubernetes Cluster under 5mins with Minikube or Docker Desktop App for Mac](https://medium.com/swlh/setup-local-kubernetes-cluster-under-5mins-with-minikube-or-docker-desktop-app-for-mac-84bd5a8ab3d6)
- [How to install Knative on minikube on mac](https://medium.com/my-engineering-notes/how-to-install-knative-on-minikube-on-mac-3c550ac56da5)
- [Setting up the Kubernetes cluster on macOS by minikube](https://subscription.packtpub.com/book/virtualization_and_cloud/9781788837606/1/ch01lvl1sec13/setting-up-the-kubernetes-cluster-on-macos-by-minikube)

# Prerequisites

- kubectl
- docker (for Mac)
- minikube
- virtualbox

### Verify

```
docker --version                
docker-compose --version        
docker-machine --version        
minikube version                
kubectl version --client        
```

### Uninstall

```
$ minikube stop
$ minikube delete
$ docker stop $(docker ps -aq)
$ docker rm -f $(docker ps -aq)
$ docker rmi $(docker images --filter "dangling=true" -q --no-trunc)

# borrar los ficheros temporales
$ rm -rf ~/.minikube ~/.kube

# Direct
$ sudo rm /usr/local/bin/minikube

$ brew uninstall minikube

$ docker stop $(docker ps | grep k8s | cut -d\  -f1)

# restart my machine
```



### Installation Guide

Brew

https://minikube.sigs.k8s.io/docs/start/macos/

https://kubernetes.io/es/docs/tasks/tools/install-minikube/

```shell
$ brew install minikube
$ minikube version
```

Upgrading minikube 

```shell
$ brew update
$ brew upgrade minikube

$ minikube version
```



Direct

- [How to Install Kubernetes on Mac](https://matthewpalmer.net/kubernetes-app-developer/articles/guide-install-kubernetes-mac.html)

- [Install Minikube on Mac Pro](https://zgljl2012.com/install-minikube-on-mac-pro/)

```
$ curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64 &&\
  chmod +x minikube &&\
  sudo mv minikube /usr/local/bin/
 
$ minikube version
```

# Start Minikube

### [virtualbox](https://minikube.sigs.k8s.io/docs/reference/drivers/virtualbox/)

As hypervisor I’m using VirtualBox which is supported on Mac, Linux and Windows.

### settings

```shell
$ minikube config set driver virtualbox
$ minikube config set disk-size 50g
$ minikube delete && minikube start --memory=4096
$ minikube addons enable ingress

# Increasing memory allocation
$ minikube config set memory 8192
$ minikube config set cpus 4
```

Check Minikube is running

```
$ minikube ip
$ minikube status
$ kubectl get services

//Kubernetes node (minikube) is ready
# To view the nodes in the cluster
$ kubectl get nodes

# see the pod states by running:
$ kubectl get po -A
```

### Kubernetes GUI

```
$ kubectl api-versions
$ minikube addons list

# Arrancar Dashboard
$ minikube dashboard
```



### Switched to context

```shell
//Kubernetes node (minikube) is ready
$ kubectl get nodes

$ brew install kubectx

# kubectl config use-context minikube
$ kubectx minikube

# Switched to context "docker-for-desktop".
$ kubectx docker-for-desktop
```



### Use minikube's built-in docker daemon:

Minikube comes with it’s own Docker daemon, so that you don’t have to use Docker Desktop. You only need the ‘docker’ CLI and point it to Minikube:

```shell
$ eval $(minikube docker-env)
```

You can revert back to the host docker daemon by running:

```shell
$ eval $(docker-machine env -u)
```



Optionally, stop the Minikube virtual machine (VM):

To stop the cluster run this command:

```
$ minikube stop
```

Optionally, delete the Minikube VM:

```
$ minikube delete
```

Check you have virtualization enabled inside your Minikube.

```
$ minikube ssh "egrep -c 'vmx|svm' /proc/cpuinfo"
```



StartHost failed, but will try again: driver start: IP address never found in dhcp leases file Temporary error: could not find an IP address



What's next
Install OpenShift