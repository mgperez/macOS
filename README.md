# macOS
```
$ brew list
$ brew cask list
$ brew cask outdated
$ brew upgrade virtualbox

% brew list | grep -i kube
kubernetes-cli
minikube


$ brew install kubernetes-cli
$ kubectl version --client  
```




# Error getting primary cp: could not find master node
```
$ minikube delete
brew uninstall minikube
# borrar los ficheros temporales
rm -rf ~/.minikube

brew install minikube
brew link minikube

$ minikube addons list
$ minikube addons enable dashboard

# Arrancar Dashboard
$ minikube dashboard
```





### Clean up

Now you can clean up the resources you created in your cluster:

```
kubectl get services
kubectl delete service hello-node

kubectl get deployments
kubectl delete deployment hello-node
```


Optionally, stop the Minikube virtual machine (VM):

```
minikube stop
```


Optionally, delete the Minikube VM:

```
minikube delete
```



### Setting Up the xhyve Driver

https://docs.okd.io/3.11/minishift/getting-started/setting-up-virtualization-environment.html

```
$ brew info --installed docker-machine-driver-xhyve
Error: `installed` cannot be passed without `json`
```



https://quarkus.io/guides/getting-started-knative

$ skaffold dev

https://kubernetes.github.io/ingress-nginx/deploy/

Instalación de Skaffold

Install kustomize

https://enmilocalfunciona.io/despliegue-validacion-microservicios-en-kubernetes-con-skaffold/

https://codersociety.com/blog/articles/build-and-deploy-kubernetes-applications-with-skaffold-and-kustomize

https://freshbrewed.science/getting-started-skaffold/index.html



```
kubectl config use-context minikube
minikube start --vm-driver=virtualbox
minikube stop
minikube start --memory=4096
minikube start --wait=false --memory=4096
minikube start --memory=4096 --cpus=2

minikube stop
https://minikube.sigs.k8s.io/docs/reference/drivers/
minikube delete && minikube start --memory=6000 --vm-driver=kvm
minikube delete && minikube start --memory=4096 --vm-driver=virtualbox

minikube delete && minikube start --memory=4096 --vm-driver=docker
```

Check Minikube is running

```
minikube status
kubectl cluster-info
kubectl get nodes
watch kubectl get pods
```

With this command, you will create a proxy server on port 8001 for accessing the Kubernetes Dashboard. It will be available at: localhost:8001/ui.

```
kubectl proxy
```

Check you have virtualization enabled inside your Minikube.

```
$ minikube ssh "egrep -c 'vmx|svm' /proc/cpuinfo"
```


minikube (include output of minikube version and kubectl version)

```
$ minikube version
```



# Installing Kubernetes with Minikube
Minikube is an easy way to try out a Kubernetes (k8s) cluster locally. It creates a single node Kubernetes stack in a local VM.

minikube dashboard
minikube addons list
minikube addons enable ingress
https://kubernetes.io/docs/tutorials/hello-minikube/

kubernetes (include output of kubectl version)

# Eclipse Che
# Installing Che with chectl
chectl server:start --installer=helm --platform=minikube
chectl server:start --platform minikube -a operator
chectl server:start --installer=operator --platform=minikube

chectl server:start --installer=operator --platform=minishift



### NGINX Ingress Controller

https://kubernetes.github.io/ingress-nginx/deploy/

Confirm the nginx-ingress-controller deployment exists:

```
$ kubectl get pods -n ingress-nginx
```

Verify installation¶
To check if the ingress controller pods have started, run the following command:

```
kubectl get pods --all-namespaces -l app.kubernetes.io/name=ingress-nginx --watch
```

# Installing che on Minikube
https://www.eclipse.org/che/docs/che-7/running-che-locally/
https://www.eclipse.org/che/docs/che-7/running-che-locally/#installing-che-on-minikube-using-chectl_running-che-locally
$ chectl server:start --platform minikube

# Kubernetes
https://docs.bitnami.com/kubernetes/get-started-kubernetes/
Watch the following video to learn how to install Kubernetes locally
https://www.katacoda.com/courses/kubernetes/launch-single-node-cluster


# Eclipse Che v7 on kubernetes cluster (not minikube)
chectl server:start -m -n che --platform=k8s
chectl server:start --platform=k8s --installer=operator

# Running Che locally
https://www.eclipse.org/che/docs/che-7/running-che-locally/
https://www.eclipse.org/che/docs/che-7/running-che-locally/#installing-che-on-minikube-using-chectl_running-che-locally


### Running Eclipse Che on Kubernetes using Docker Desktop
https://che.eclipse.org/running-eclipse-che-on-kubernetes-using-docker-desktop-for-mac-5d972ed511e1
brew install kubernetes-helm
helm version

You can now check that Eclipse Che server is running
$ kubectl get pod --namespace che
$ kubectl logs -f che-7b68bcc94b-fpbhz -n che
$ kubectl get events --namespace che  -o custom-columns=TIMESTAMP:lastTimestamp,TYPE:type,MESSAGE:message -w

kubectl delete namespace che
minikube start --memory=4096 --vm-driver=docker
chectl server:start --platform=minikube


https://che.eclipse.org/eclipse-che-7-is-now-available-40ae07120b38


https://www.katacoda.com/courses/kubernetes/launch-single-node-cluster

Openshift (include output of oc version)
minishift (include output of minishift version and oc version)
docker-desktop + K8S (include output of docker version and kubectl version)


https://github.com/eclipse/che-operator/tree/master/olm
testupdate kubernetes stable che



### How to Run Minishift

http://keyangxiang.com/2018/05/18/Openshift/how-to-run-minishift-on-macos/

- [Troubleshooting Getting Started](https://docs.okd.io/3.11/minishift/troubleshooting/troubleshooting-getting-started.html)

```
# let’s start minishift:
$ minishift start --vm-driver=virtualbox --memory=6G --cpus=4

# To shutdown your minishift cluster simply run:
$ minishift stop

# Error during setting 'minishift' as active profile: The specified path to the kube config '/home/laurence/.minishift/machines/minishift_kubeconfig' does not exist 
minishift delete -f
minishift start --profile minishift

# v3.11.0 is not a valid OpenShift versionFAIL
$ minishift config set skip-check-openshift-release true
# Error starting the cluster: Error attempting to download and cache 'oc'

```

- [From zero to Quarkus and Knative: The easy way](https://developers.redhat.com/blog/2019/04/09/from-zero-to-quarkus-and-knative-the-easy-way/)
- [QUICK GUIDE TO MICROSERVICES WITH QUARKUS ON OPENSHIFT](https://piotrminkowski.com/2019/08/23/quick-guide-to-microservices-with-quarkus-on-openshift/)



Tutorial: Java and Maven in Eclipse Che

https://dzone.com/articles/tutorial-java-amp-maven-in-eclipse-che