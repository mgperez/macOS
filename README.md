# macOS
$ brew list
$ brew cask list
$ brew cask outdated
$ brew upgrade virtualbox

% brew list | grep -i kube
kubernetes-cli
minikube


$ brew install kubernetes-cli
$ kubectl version --client  

# Error getting primary cp: could not find master node
brew uninstall minikube
rm -rf ~/.minikube
brew install minikube
brew link minikube

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

Check Minikube is running
kubectl cluster-info
kubectl get nodes

With this command, you will create a proxy server on port 8001 for accessing the Kubernetes Dashboard. It will be available at: localhost:8001/ui.
kubectl proxy

Check you have virtualization enabled inside your Minikube.
$ minikube ssh "egrep -c 'vmx|svm' /proc/cpuinfo"

$ minikube version
minikube (include output of minikube version and kubectl version)

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

# Installing che on Minikube
$ chectl server:start --platform minikube

# Eclipse Che v7 on kubernetes cluster (not minikube)
chectl server:start -m -n che --platform=k8s
chectl server:start --platform=k8s --installer=operator

# Running Eclipse Che on Kubernetes using Docker Desktop
https://che.eclipse.org/running-eclipse-che-on-kubernetes-using-docker-desktop-for-mac-5d972ed511e1
brew install kubernetes-helm
helm version

You can now check that Eclipse Che server is running
$ kubectl get pod --namespace che
$ kubectl logs -f che-7b68bcc94b-fpbhz -n che

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

