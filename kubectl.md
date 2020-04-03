# Installing kubectl

https://rancher.com/learning-paths/how-to-manage-kubernetes-with-kubectl/

https://kubernetes.io/docs/tasks/tools/install-kubectl/

```
% brew list | grep -i kube
kubernetes-cli
minikube


# Installing kubectl
$ brew install kubernetes-cli

# Test to ensure the version you installed is up-to-date:
$ kubectl version --short
$ kubectl version --client


# To view the current configuration, type:
$ kubectl config view

# To quickly just check on the current context being used, type:
$ kubectl config get-contexts
$ kubectl config current-context

# Checking the Status of Cluster Components
$ kubectl get cs
```

### Check Minikube is running

```
# Verifying kubectl configuration
$ kubectl cluster-info
$ kubectl get nodes -o wide

# create a deployment called nginx which runs a container based off of the default nginx container image. 
$ kubectl create deploy nginx --image=nginx

# listing the currently deployed pods:
$ kubectl get pods
$ kubectl get pod --all-namespaces

$ kubectl get ns
```



### Deployment

```
# create a deployment called nginx which runs a container based off of the default nginx container image. 

$ kubectl create deploy nginx --image=nginx

# listing the currently deployed pods:

$ kubectl get pods
$ kubectl get pod --all-namespaces

# clean up the deployed resources by typing:

$ kubectl delete deployment nginx
```



### Clean up

Now you can clean up the resources you created in your cluster:

```
kubectl get pods

kubectl get services
kubectl delete service hello-node

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