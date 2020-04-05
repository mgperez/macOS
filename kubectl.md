# Kubernetes (K8s)

https://rancher.com/learning-paths/how-to-manage-kubernetes-with-kubectl/

Uninstall

```
$ brew uninstall kubernetes-cli
$ sudo rm -rf ~/.kube

# Direct
$ sudo rm /usr/local/bin/kubectl
```



### Installation Guide

https://kubernetes.io/docs/tasks/tools/install-kubectl/

Brew

```
% brew list | grep -i kube
kubernetes-cli

# Installing kubectl
$ brew install kubernetes-cli
$ brew pin kubernetes-cli

# check installed package by homebrew
$ brew list | grep kube
```



Direct

https://zgljl2012.com/install-minikube-on-mac-pro/

Download the latest kubectl

```bash
cd ~/Downloads

curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/darwin/amd64/kubectl
```

change the permission，move to `$PATH`

```bash
chmod +x ~/Downloads/kubectl

mv ~/Downloads/kubectl /usr/local/bin/

kubectl --help
```



```

# Test to ensure the version you installed is up-to-date:
$ kubectl version --short
$ kubectl version --client


# To view the current configuration, type:
$ kubectl config view

# To quickly just check on the current context being used, type:
$ kubectl config get-contexts
$ kubectl config current-context

# Checking the Status of Cluster Components
# get cs will shows Component Status
$ kubectl get cs
```



Switched to context

```
//Kubernetes node (minikube) is ready
$ kubectl get nodes

$ kubectl config use-context minikube
rm -rf ~/.kube/cache
[user@k8s-master ~]# mkdir -p $HOME/.kube
[user@k8s-master ~]# cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
[user@k8s-master ~]# chown $(id -u):$(id -g) $HOME/.kube/config

export KUBECONFIG=/etc/kubernetes/admin.conf

# Make sure it removes all the containers
$ docker stop $(docker ps -aq)
$ docker rm -f $(docker ps -aq)

# After you make sure all the containers have been removed, restart kubelet
$ systemctl restart kubelet


# Switched to context "docker-for-desktop".
$ kubectl config use-context docker-for-desktop
```



### Check Minikube is running

```
# Verifying kubectl configuration
$ kubectl cluster-info
$ kubectl get ns
$ kubectl get nodes -o wide
$ kubectl get all

# listing the currently deployed pods:
$ kubectl get pods
$ kubectl get pod --all-namespaces
# see the pod states by running:
$ kubectl get po -A

# listing services
$ kubectl get svc
```



### Deployment

```
# create a deployment called nginx which runs a container based off of the default nginx container image. 
$ kubectl create deploy nginx --image=nginx

# View the Deployment:
$ kubectl get deployments

# View the Pod: 
$ kubectl get pods

# View cluster events:
$ kubectl get events

# View the kubectl configuration:
$ kubectl config view

# clean up the deployed resources by typing:
$ kubectl delete deployment nginx
```



### Clean up

Now you can clean up the resources you created in your cluster:

```
kubectl get pods

kubectl get services
kubectl delete service hello-node
$ kubectl delete services hello-world

kubectl get deployments
kubectl delete deployment hello-node

```



### NGINX Ingress Controller

https://kubernetes.github.io/ingress-nginx/deploy/

Confirm the nginx-ingress-controller deployment exists:

```
$ kubectl get pods -n ingress-nginx
```

Verify installation
To check if the ingress controller pods have started, run the following command:

```
$ kubectl get pods --all-namespaces -l app.kubernetes.io/name=ingress-nginx --watch
```



### Eclipse Che

You can now check that Eclipse Che server is running

```
$ kubectl get pod --namespace che
$ kubectl logs -f che-7b68bcc94b-fpbhz -n che
$ kubectl get events --namespace che  -o custom-columns=TIMESTAMP:lastTimestamp,TYPE:type,MESSAGE:message -w

$ kubectl delete namespace che
```

With this command, you will create a proxy server on port 8001 for accessing the Kubernetes Dashboard. It will be available at: localhost:8001/ui.

```
kubectl proxy
```



What's next
Install Minikube