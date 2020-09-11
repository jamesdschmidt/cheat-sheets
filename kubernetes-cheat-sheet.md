# Kubernetes Cheat Sheet

## Clusters

List clusters
```
kind get clusters
```

Delete cluster (default kind cluster)
```
kind delete cluster
```

Delete named cluster
```
kind delete cluster --name <cluster-name>
```

## Pods

List pods
```
kubectl get pods
```

Delete pod
```
kubectl delete pod <pod-name>
```
