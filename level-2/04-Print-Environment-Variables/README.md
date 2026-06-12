# Print Envars Greeting Pod

This Kubernetes pod demonstrates how to define environment variables and run a simple command to print a greeting message.

## Objective

Create a pod named `print-envars-greeting` that:

* Uses container name `print-env-container` with the `bash` image.
* Defines three environment variables:

  * `GREETING=Welcome to`
  * `COMPANY=Stratos`
  * `GROUP=Ltd`
* Runs the command:
  `/bin/sh -c 'echo "$(GREETING) $(COMPANY) $(GROUP)"'`
* Uses `restartPolicy: Never` to avoid crash loops.
* Output can be viewed using:

```bash
kubectl logs -f print-envars-greeting
```

## Files

* `pod.yaml` – Kubernetes pod definition.
* `README.md` – Documentation for the pod.

## Usage

### Create the Pod

```bash
kubectl apply -f pod.yaml
```

### Verify Pod Status

```bash
kubectl get pods
```

Expected status:

```text
Completed
```

### View Logs

```bash
kubectl logs -f print-envars-greeting
```

### Delete the Pod

```bash
kubectl delete -f pod.yaml
```
### Verification Commands

kubectl apply -f pod.yaml
kubectl get pods
kubectl logs -f print-envars-greeting
kubectl delete -f pod.yaml

### Expected output:
Welcome to Stratos Ltd

## Notes

* The pod executes the command once and exits.

