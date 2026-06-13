# Kubernetes Rolling Update and Rollback

## Objective

This lab demonstrates how to perform a rolling update and rollback in Kubernetes using a Deployment.

## Tasks Performed

1. Created a namespace named `xfusion`.
2. Created a Deployment named `httpd-deploy`.
3. Configured RollingUpdate strategy:

   * maxSurge: 1
   * maxUnavailable: 2
4. Created a NodePort Service named `httpd-service`.
5. Exposed the application on NodePort `30008`.
6. Upgraded the application image from `httpd:2.4.28` to `httpd:2.4.43`.
7. Verified the rollout status.
8. Rolled back the Deployment to the previous stable version.

## Resources Created

### Namespace

* xfusion

### Deployment

* Name: httpd-deploy
* Image: httpd:2.4.28
* Replicas: 3

### Service

* Name: httpd-service
* Type: NodePort
* NodePort: 30008

## Rolling Update

Upgrade command:

```bash
kubectl set image deployment/httpd-deploy httpd=httpd:2.4.43 -n xfusion
```

Verify rollout:

```bash
kubectl rollout status deployment/httpd-deploy -n xfusion
```

## Rollback

Rollback command:

```bash
kubectl rollout undo deployment/httpd-deploy -n xfusion
```

Verify image:

```bash
kubectl get deployment httpd-deploy -n xfusion -o=jsonpath='{.spec.template.spec.containers[0].image}'
```

Expected output:

```text
httpd:2.4.28
```

## Learning Outcome

* Kubernetes Deployment Management
* Rolling Updates
* Rollback Operations
* Service Exposure using NodePort
* Deployment Revision History

