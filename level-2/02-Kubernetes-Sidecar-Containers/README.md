# Kubernetes Sidecar Containers

## Objective

Create a Kubernetes Pod named `webserver` with:

* Main container: `nginx-container` using `nginx:latest`
* Sidecar init container: `sidecar-container` using `ubuntu:latest`
* Shared volume: `shared-logs` (`emptyDir`)
* Mount path: `/var/log/nginx`

The sidecar container continuously reads Nginx access and error logs from the shared volume.

## Architecture

Pod: webserver

* nginx-container (Web Server)
* sidecar-container (Log Collector)
* shared-logs (emptyDir Volume)

## Deployment

Apply the manifest:

kubectl apply -f pod.yaml

Verify:

kubectl get pods

kubectl describe pod webserver

## Result

Successfully deployed the pod with:

* nginx-container
* sidecar-container
* shared emptyDir volume

Pod Status: Running

## Key Concepts Learned

* Sidecar Container Pattern
* Init Containers
* Shared Volumes (emptyDir)
* Container Log Collection
* Kubernetes Pod Design

