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



### Deploy an app

```
# create a deployment called nginx which runs a container based off of the default nginx container image. 
$ kubectl create deploy nginx --image=nginx
$ kubectl create deployment kubernetes-bootcamp --image=gcr.io/google-samples/kubernetes-bootcamp:v1

# View the Deployment:
$ kubectl get deployments



```

### Explore your app

```shell
#  look for existing Pods: 
$ kubectl get pods

# to view what containers are inside that Pod and what images are used to build those containers 
$ kubectl describe pods





# View cluster events:
$ kubectl get events

# View the kubectl configuration:
$ kubectl config view

# clean up the deployed resources by typing:
$ kubectl delete deployment nginx
```

#### Show the app in the terminal

Recall that Pods are running in an isolated, private network - so we need to proxy access to them so we can debug and interact with them. To do this, we'll use the `kubectl proxy` command to run a proxy in a second terminal window. Click on the command below to automatically open a new terminal and run the `proxy`:

```
$ echo -e "\n\n\n\e[92mStarting Proxy. After starting it will not output a response. Please click the first Terminal Tab\n"; 
$ kubectl proxy
```

Now again, we'll get the Pod name and query that pod directly through the proxy. To get the Pod name and store it in the POD_NAME environment variable:

```
$ export POD_NAME=$(kubectl get pods -o go-template --template '{{range .items}}{{.metadata.name}}{{"\n"}}{{end}}') 
$ echo Name of the Pod: $POD_NAME
```

#### Module 4 - Expose your app publicly

#### Step 1 Create a new service

```
# look for existing Pods:
# Let’s verify that our application is running.
$ kubectl get pods

# list the current Services from our cluster:
$ kubectl get services
```

We have a Service called kubernetes that is created by default when minikube starts the cluster. To create a new service and expose it to external traffic we’ll use the expose command with NodePort as parameter (minikube does not support the LoadBalancer option yet).

```
$ kubectl expose deployment/kubernetes-bootcamp --type="NodePort" --port 8080
$ kubectl expose deployment/hello-jakartaee --type="NodePort" --port 8080

# list the current Services from our cluster:
$ kubectl get services
```

We have now a running Service called kubernetes-bootcamp. Here we see that the Service received a unique cluster-IP, an internal port and an external-IP (the IP of the Node).

To find out what port was opened externally (by the NodePort option) we’ll run the `describe service` command:

```
kubectl describe services/kubernetes-bootcamp
kubectl describe services/hello-jakartaee

# Create an environment variable called NODE_PORT that has the value of the Node port assigned:
$ export NODE_PORT=$(kubectl get services/kubernetes-bootcamp -o go-template='{{(index .spec.ports 0).nodePort}}')

$ export NODE_PORT=$(kubectl get services/hello-jakartaee -o go-template='{{(index .spec.ports 0).nodePort}}')

$ echo NODE_PORT=$NODE_PORT

# Now we can test that the app is exposed outside of the cluster using curl, the IP of the Node and the externally exposed port:
$ curl $(minikube ip):$NODE_PORT
$ curl $(minikube ip):$NODE_PORT/hello-jakartaee/api/hello
```

#### Step 2: Using labels

```
# see the name of the label:
$ kubectl describe deployment

# Let’s use this label to query our list of Pods.
$ kubectl get pods -l app=kubernetes-bootcamp

# to list the existing services:
$ kubectl get services -l app=kubernetes-bootcamp

# Get the name of the Pod and store it in the POD_NAME environment variable:
$ export POD_NAME=$(kubectl get pods -o go-template --template '{{range .items}}{{.metadata.name}}{{"\n"}}{{end}}')
$ echo Name of the Pod: $POD_NAME
```

To apply a new label we use the label command followed by the object type, object name and the new label:

```
$ kubectl label pod $POD_NAME app=v1
```

This will apply a new label to our Pod (we pinned the application version to the Pod), and we can check it with the describe pod command:

```
$ kubectl describe pods $POD_NAME
```

We see here that the label is attached now to our Pod. And we can query now the list of pods using the new label:

```
$ kubectl get pods -l app=v1
```

#### Step 3 Deleting a service

```
# To delete Services
$ kubectl delete service -l app=kubernetes-bootcamp

# Confirm that the service is gone:
# This confirms that our Service was removed.
$ kubectl get services

# To confirm that route is not exposed anymore you can curl the previously exposed IP and port:
$ curl $(minikube ip):$NODE_PORT
```

This proves that the app is not reachable anymore from outside of the cluster. You can confirm that the app is still running with a curl inside the pod:

```
kubectl exec -ti $POD_NAME curl localhost:8080
```

We see here that the application is up. This is because the Deployment is managing the application. To shut down the application, you would need to delete the Deployment as well.



Kubernetes

```shell
# With this command, we will create the deployment.
$> kubectl apply -f deployment.yml
$ kubectl get pods -Lapp -Ltier -Lrole
$ kubectl get pods -lapp=<hello-jakartaee>,role=<slave>

# Now run the following command to see if the deployment was created.
$> kubectl get deployments

# The following command will list all the services.
$> kubectl get services
# When you run this command, you will see which port the app is running on Kubernetes.
NAME              PORT(S)
hello-jakartaee   8080:30549/TCP
```

Open your browser and point it to http://localhost:30549/hello-jakartaee/api/hello



### Clean up

Now you can clean up the resources you created in your cluster:

```shell
# to delete the same resources you created:
$ kubectl delete -f deployment.yml

kubectl get services
$ kubectl delete services hello-world

kubectl get deployments
$ kubectl delete deployment hello-node

# to filter resources by their labels:
$ kubectl get pods -Lapp -Ltier -Lrole
$ kubectl delete deployment,services -l app=hello-jakartaee

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