# Instalar Minikube

https://kubernetes.io/es/docs/tasks/tools/install-minikube/

https://gist.github.com/kevin-smets/b91a34cea662d0c523968472a81788f7

https://minikube.sigs.k8s.io/docs/start/macos/

- [Setup Local Kubernetes Cluster under 5mins with Minikube or Docker Desktop App for Mac](https://medium.com/swlh/setup-local-kubernetes-cluster-under-5mins-with-minikube-or-docker-desktop-app-for-mac-84bd5a8ab3d6)
- [How to install Knative on minikube on mac?](https://medium.com/my-engineering-notes/how-to-install-knative-on-minikube-on-mac-3c550ac56da5)
- [Setting up the Kubernetes cluster on macOS by minikube](https://subscription.packtpub.com/book/virtualization_and_cloud/9781788837606/1/ch01lvl1sec13/setting-up-the-kubernetes-cluster-on-macos-by-minikube)

# Prerequisites

- Instalar un Hipervisor ???
- Instalar kubectl

Uninstall Hipervisor

```
$ brew uninstall docker-machine-driver-hyperkit


$ brew uninstall hyperkit
rm '/usr/local/bin/hyperkit'
brew link --overwrite hyperkit
brew link --overwrite --dry-run hyperkit
brew unlink hyperkit && brew link hyperkit
```



## Install docker-machine-driver-hyperkit

```bash
brew update
brew install hyperkit
brew install docker-machine-driver-hyperkit

sudo chown root:wheel $(brew --prefix)/opt/docker-machine-driver-hyperkit/bin/docker-machine-driver-hyperkit
sudo chmod u+s $(brew --prefix)/opt/docker-machine-driver-hyperkit/bin/docker-machine-driver-hyp

$ brew list | grep hyper
```

# Verify

```
docker --version                
docker-compose --version        
docker-machine --version        
minikube version                
kubectl version --client        
```

Uninstall

```
$ minikube stop
$ minikube delete
$ docker stop $(docker ps -aq)
$ docker rm -f $(docker ps -aq)

# borrar los ficheros temporales
rm -rf ~/.minikube
sudo rm /usr/local/bin/minikube

docker stop $(docker ps | grep k8s | cut -d\  -f1)
```



Install Minikube via the Installation > OSX instructions from the latest release. At the time of writing, this meant running the following command in Terminal…

https://matthewpalmer.net/kubernetes-app-developer/articles/guide-install-kubernetes-mac.html



[Install Minikube on Mac Pro](https://zgljl2012.com/install-minikube-on-mac-pro/)

```
(1)***$ curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64 &&\
  chmod +x minikube &&\
  sudo mv minikube /usr/local/bin/
 
$ minikube version
```

# Start Minikube

```
$ minikube delete && minikube start --memory=4096 --vm-driver=docker
```



```
# The 'hyperkit' driver requires elevated permissions. The following commands will be executed:
$ sudo chown root:wheel /Users/marcialgarciaperez/.minikube/bin/docker-machine-driver-hyperkit
$ sudo chmod u+s /Users/marcialgarciaperez/.minikube/bin/docker-machine-driver-hyperkit

$ minikube delete && minikube start


StartHost failed, but will try again: creating host: create: Error creating machine: Error in driver during machine creation: IP address never found in dhcp leases file Temporary error: could not find an IP address for d6:ea:4:2c:52:2
🔥  Eliminando "minikube" en hyperkit..



$ minikube start --vm-driver=hyperkit



$ kubectl config use-context minikube
$ minikube delete && minikube start --vm-driver=hyperkit  
$ minikube start
```

Check Minikube is running

```
$ minikube status

//Kubernetes node (minikube) is ready
$ kubectl get nodes
```



Arrancar Dashboard

```
$ kubectl api-versions
$ minikube addons list

# Arrancar Dashboard
$ minikube dashboard
```

Optionally, stop the Minikube virtual machine (VM):

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



### Minikube

- [Hello Minikube](https://kubernetes.io/docs/tutorials/hello-minikube/)
- [Quarkus: A quick-start guide to the Kubernetes-native Java stack](https://developers.redhat.com/articles/quarkus-quick-start-guide-kubernetes-native-java-stack/)



What's next
Install OpenShift