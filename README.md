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

$ minikube version

# Installing Kubernetes with Minikube
minikube dashboard
minikube addons list
minikube addons enable ingress

chectl server:start --installer=helm --platform=minikube
chectl server:start --installer=minikube
