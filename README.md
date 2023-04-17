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

Get a Kubernetes deployments to check the status:

```bash
kubectl get deployments
```
