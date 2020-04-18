# macOS



[Bash script to upgrade packages](https://apple.stackexchange.com/questions/190072/is-there-any-way-to-upgrade-brew-cask/231020#231020)

```
curl -s https://gist.githubusercontent.com/atais/9c72e469b1cbec35c7c430ce03de2a6b/raw/36808a0544628398f26b48f7a3c7b309872ca2c6/cask_upgrade.sh | bash /dev/stdin
```

**save as** `/usr/local/bin/cask-upgrade`, so you can run it locally as `cask-upgrade` later

```
$ cd /Applications/dev
$ ./cask_upgrade.sh
$ brew list
```

Homebrew-Cask

```
$ brew cask list
$ brew cask outdated
```



VirtualBox

Install VirtualBox for Mac using Homebrew

```shell
$ brew cask install virtualbox
```

Upgrading VirtualBox 

```shell
$ brew cask outdated
$ brew cask upgrade virtualbox
```



## Prerequisites

### Get started with Docker Desktop for Mac

https://docs.docker.com/docker-for-mac/install/

https://docs.docker.com/toolbox/toolbox_install_mac/

- [Install on MacOS by berlioz | Katacoda](https://www.katacoda.com/berlioz/scenarios/install-on-mac)

- [Docker Desktop](https://hub.docker.com/search?q=&type=edition&offering=community&sort=updated_at&order=desc)



### What is DBeaver?

https://www.code2bits.com/how-to-install-dbeaver-community-on-macos-using-homebrew/

dbeaver-community requires Java 8+. You can install the latest version with:
  brew cask install adoptopenjdk

### Failed to create java virtual machine .

Edit /Applications/DBeaver.app/Contents/Info.plist file, and add jdk path like this:

```
<key>Eclipse</key>
  <array>
    <string>-vm</string>
    <string>/Library/Java/JavaVirtualMachines/jdk1.8.0_202.jdk/Contents/Home/bin/java</string>
    <!-- Other properties left out-->
  </array>
```



## Usage

Start a cluster using the docker driver:

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