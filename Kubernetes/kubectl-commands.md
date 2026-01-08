
# `kubectl` Commands Cheat Sheet

## Overview
`kubectl` is the command-line tool used to interact with Kubernetes clusters.  
It communicates with the Kubernetes API server to deploy applications, inspect resources, and manage clusters.

---

## Basic kubectl Commands

### Check Cluster Info
```bash
kubectl cluster-info
````

### Check Client and Server Versions

```bash
kubectl version
kubectl version --client
```

### Get Nodes

```bash
kubectl get nodes
kubectl get nodes -o wide
```

---

## Working with Namespaces

### List Namespaces

```bash
kubectl get namespaces
```

### Create a Namespace

```bash
kubectl create namespace dev
```

### Use a Namespace

```bash
kubectl config set-context --current --namespace=dev
```

---

## Working with Pods

### List Pods

```bash
kubectl get pods
kubectl get pods -o wide
```

### Describe a Pod

```bash
kubectl describe pod <pod-name>
```

### View Pod Logs

```bash
kubectl logs <pod-name>
kubectl logs <pod-name> -c <container-name>
```

### Execute Command Inside a Pod

```bash
kubectl exec -it <pod-name> -- /bin/sh
```

---

## Working with Deployments

### Create a Deployment

```bash
kubectl create deployment nginx --image=nginx
```

### List Deployments

```bash
kubectl get deployments
```

### Describe Deployment

```bash
kubectl describe deployment nginx
```

### Scale a Deployment

```bash
kubectl scale deployment nginx --replicas=3
```

### Update Image

```bash
kubectl set image deployment/nginx nginx=nginx:latest
```

---

## Working with Services

### List Services

```bash
kubectl get services
```

### Expose a Deployment

```bash
kubectl expose deployment nginx --type=NodePort --port=80
```

### Describe a Service

```bash
kubectl describe service nginx
```

---

## ConfigMaps and Secrets

### Create ConfigMap

```bash
kubectl create configmap app-config --from-literal=APP_ENV=prod
```

### Create Secret

```bash
kubectl create secret generic db-secret --from-literal=password=12345
```

### View ConfigMaps and Secrets

```bash
kubectl get configmaps
kubectl get secrets
```

---

## Apply and Delete Resources

### Apply a YAML File

```bash
kubectl apply -f app.yaml
```

### Delete a Resource

```bash
kubectl delete pod <pod-name>
kubectl delete deployment nginx
```

### Delete Using YAML

```bash
kubectl delete -f app.yaml
```

---

## Debugging and Troubleshooting

### Describe Resources

```bash
kubectl describe pod <pod-name>
kubectl describe node <node-name>
```

### Check Events

```bash
kubectl get events
```

### Check Resource Usage (Metrics Server Required)

```bash
kubectl top nodes
kubectl top pods
```

---

## Labels and Selectors

### Add a Label

```bash
kubectl label pod <pod-name> env=dev
```

### Filter by Label

```bash
kubectl get pods -l env=dev
```

---

## Rolling Updates and Rollbacks

### Check Rollout Status

```bash
kubectl rollout status deployment/nginx
```

### View Rollout History

```bash
kubectl rollout history deployment/nginx
```

### Rollback Deployment

```bash
kubectl rollout undo deployment/nginx
```

---

## Context and Cluster Management

### View Current Context

```bash
kubectl config current-context
```

### List Contexts

```bash
kubectl config get-contexts
```

### Switch Context

```bash
kubectl config use-context <context-name>
```

---

## Advanced kubectl Commands

### Dry Run

```bash
kubectl apply -f app.yaml --dry-run=client
```

### Output Formats

```bash
kubectl get pods -o yaml
kubectl get pods -o json
```

### Watch Resources

```bash
kubectl get pods -w
```

---

## Useful Shortcuts

| Command  | Description |
| -------- | ----------- |
| `po`     | pods        |
| `svc`    | services    |
| `deploy` | deployments |
| `ns`     | namespaces  |

Example:

```bash
kubectl get po
kubectl get svc
```

---

## Conclusion

Mastering `kubectl` commands is essential for working efficiently with Kubernetes. This cheat sheet covers the most commonly used commands for day-to-day operations.

---

## References

* [https://kubernetes.io/docs/reference/kubectl/](https://kubernetes.io/docs/reference/kubectl/)
* [https://kubernetes.io/docs/tasks/tools/](https://kubernetes.io/docs/tasks/tools/)

