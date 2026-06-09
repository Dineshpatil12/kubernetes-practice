# Day 03: Deploy Nginx Web Server on Kubernetes Cluster

## Objective

Deploy an Nginx web server using a Kubernetes Deployment with multiple replicas and expose it using a NodePort Service.

## Requirements

* Deployment Name: nginx-deployment
* Container Name: nginx-container
* Image: nginx:latest
* Replicas: 3
* Service Name: nginx-service
* Service Type: NodePort
* NodePort: 30011

## Files

* pod.yaml

## Commands Used

Create resources:

kubectl apply -f pod.yaml

Verify deployment:

kubectl get deployment nginx-deployment

Verify pods:

kubectl get pods

Verify service:

kubectl get svc nginx-service

## Expected Result

* Deployment running with 3 replicas.
* Nginx container uses nginx:latest image.
* Service exposed through NodePort 30011.
* All pods are in Running state.

## Learning Outcome

* Kubernetes Deployment creation.
* Replica management.
* Service exposure using NodePort.
* Basic application deployment in Kubernetes.

