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

List details of cluster
```
% kubectl get all -A
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

## Nodes

List nodes
```
% kubectl get nodes
```

## Pods

Create a pod
```
% kubectl apply -f pod.yaml
```

List pods
```
% kubectl get pods
```

Get details of pod
```
% kubectl describe pod <pod-name>
```

Delete a pod
```
% kubectl delete pod <pod-name>
```

Delete a pod (alternate)
```
% kubectl delete -f pod.yaml
```
