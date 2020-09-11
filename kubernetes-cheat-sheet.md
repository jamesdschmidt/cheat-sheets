# Kubernetes Cheat Sheet

## Clusters

Create a cluster (default kind cluster)
```
% kind create cluster
```

List clusters
```
% kind get clusters
```

Get cluster information
```
% kubectl cluster-info
```

Delete a cluster (default kind cluster)
```
% kind delete cluster
```

Delete a named cluster
```
% kind delete cluster --name <cluster-name>
```

## Contexts

List contexts
```
% kubectl config get-contexts
```

## Pods

List pods
```
% kubectl get pods
```

Delete a pod
```
% kubectl delete pod <pod-name>
```
