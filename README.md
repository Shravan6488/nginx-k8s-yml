# Kubernetes on Local with Minikube Tutorial

## Install
You need to install in your machine :
- Docker (https://docs.docker.com/engine/installation/)
- Minikube (https://github.com/kubernetes/minikube/releases) And the requirement of minikube (https://github.com/kubernetes/minikube#installation)


## Let's Play

### Starting ...

First start minikube that will run in local kubernetes (instead have to use google cloud or AWS )
```bash
minikube start
```

Check that Kubernetes are running well 
```bash
kubectl cluster-info
```

### First example :
For your first example you can follow the one given by minikube itself : https://github.com/kubernetes/minikube#quickstart

### Second example :
We will do more fun things that this first example.
Once minikube is started you can do everything kubernetes allow (there are a lot of tutorial in internet) with some differences that we will see throught an example :

Let's begin by creating 2 replication of an nginx docker load balanced on Kubernetes.

```bash
git clone https://github.com/Shravan6488/nginx-k8s-yml.git
cd nginx-k8s-yml
kubectl apply -f k8s_nginx.yml'
```
You can see your 2 replicas some seconds later "running" by typing 

```bash
kubectl get pod
```

Once it's running you can see their internal IP 
```bash
kubectl get services
```

You can't see their external IP, because it's running in a minikube
To Test you can find the minikube ip by typing in your browser and port as 80 : 
```bash
http://MINIKBE-IP
```
![ngnix_screen](/nginx.png)


#### Playing with replicas

Let's delete one of our pod, and see how kubernetes behave :
So get the name of one of your pods typing :
```bash
kubectl get pod
```

Once you have the name :

```bash
kubectl delete pod [name]
```

And right after you will see kubernetes creating an other container to continue having 2 replicas :
```bash
kubectl get pod
```

#### Entering in a container

check the name of your pods
```bash
kubectl get pod
```

Execute the following command with the name of your first pod.
```bash
kubectl exec -ti  [PODname] --bash
```
