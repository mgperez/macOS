# macOS



[Bash script to upgrade packages](https://apple.stackexchange.com/questions/190072/is-there-any-way-to-upgrade-brew-cask/231020#231020)

```
curl -s https://gist.githubusercontent.com/atais/9c72e469b1cbec35c7c430ce03de2a6b/raw/36808a0544628398f26b48f7a3c7b309872ca2c6/cask_upgrade.sh | bash /dev/stdin
```

**save as** `/usr/local/bin/cask-upgrade`, so you can run it locally as `cask-upgrade` later

```
$ cd /Applications/dev
$ ./cask_upgrade.sh
```



```
$ brew list


$ brew upgrade virtualbox

```

Homebrew-Cask

```
$ brew cask list
$ brew cask outdated
```



## Prerequisites

### Get started with Docker Desktop for Mac

https://docs.docker.com/docker-for-mac/install/

https://docs.docker.com/toolbox/toolbox_install_mac/

[Install on MacOS by berlioz | Katacoda](https://www.katacoda.com/berlioz/scenarios/install-on-mac)



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

# Installing Kubernetes with Minikube
Minikube is an easy way to try out a Kubernetes (k8s) cluster locally. It creates a single node Kubernetes stack in a local VM.

minikube addons list
minikube addons enable ingress

# Eclipse Che
# Installing Che with chectl
chectl server:start --installer=helm --platform=minikube
chectl server:start --platform minikube -a operator
chectl server:start --installer=operator --platform=minikube

chectl server:start --installer=operator --platform=minishift



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


minikube start --memory=4096 --vm-driver=docker
chectl server:start --platform=minikube


https://che.eclipse.org/eclipse-che-7-is-now-available-40ae07120b38


https://www.katacoda.com/courses/kubernetes/launch-single-node-cluster

Openshift (include output of oc version)
minishift (include output of minishift version and oc version)
docker-desktop + K8S


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