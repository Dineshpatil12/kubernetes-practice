# Kubernetes Shared Volumes

## Objective

Create a Kubernetes Pod with two containers that share the same storage using an `emptyDir` volume.

## Task Requirements

* Create a Pod named `volume-share-devops`
* Use two containers with image `debian:latest`
* Create a shared volume named `volume-share`
* Mount the volume in both containers:

  * `/tmp/blog`
  * `/tmp/demo`
* Create a file in the first container and verify it is accessible from the second container

---

## Pod Manifest

File: `pod.yaml`

### Volume Type

```yaml
emptyDir: {}
```

The `emptyDir` volume is created when the Pod starts and is shared among all containers in the Pod.

---

## Deployment

Create the Pod:

```bash
kubectl apply -f pod.yaml
```

Verify:

```bash
kubectl get pods
```

Output:

```text
NAME                  READY   STATUS    RESTARTS   AGE
volume-share-devops   2/2     Running   0          12s
```

---

## Verification

Create the test file:

```bash
kubectl exec -it volume-share-devops -c volume-container-devops-1 -- /bin/bash
```

Inside the container:

```bash
echo "Welcome to xFusionCorp Industries" > /tmp/blog/blog.txt
```

Verify from the second container:

```bash
kubectl exec -it volume-share-devops -c volume-container-devops-2 -- cat /tmp/demo/blog.txt
```

Output:

```text
Welcome to xFusionCorp Industries
```

---

## Key Concepts

### emptyDir

* Created when a Pod starts.
* Shared by all containers in the Pod.
* Stores temporary data.
* Deleted automatically when the Pod is removed.

### Volume Mounts

Volume mounts allow containers to access a shared storage location inside the Pod.

---

## Result

Successfully created a multi-container Pod using a shared `emptyDir` volume and verified data sharing between containers.

