# Deploying Application on Kubernetes

This guide explains how to deploy the sample application on a Kubernetes cluster.

## Prerequisites

Before you get started, you need to have the following tools installed:

- Docker
- minikube or a Kubernetes cluster
- kubectl

## Building the app image

Navigate to the root directory of the cloned repository:

Build the Docker image and push it to a registry:

```bash
docker build -t kubernates-app .

# rename and push the image to docker registry so that the kubernate cluster can pull it (username is your registry username)
docker tag kubernates-app username/kubernates-app
docker push username/kubernates-app
```

Create a Kubernetes deployment:

```bash
kubectl create deployment kubernates-app --image=username/kubernates-app
```

To Get a Kubernetes deployments and check the status, run:

```bash
kubectl get deployments
```

Expose the deployment as a Kubernetes service:

```bash
kubectl expose deployment kubernates-app --type=LoadBalancer --port=8080
```

Get the external IP address of the service:

```bash
kubectl get services
# the kubernates-app service will have pending external ip because we use minikube in local
# to get an external ip for the kubernates-app service and open the generated url in the browser
minikube service kubernates-app
```

Scaling to 3 pods/containers:

```bash
kubectl scale deployment/kubernates-app --replicas=3
```
