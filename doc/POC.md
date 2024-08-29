# Install ArgoCD and login

### Create namespace ArgoCD
```shell
kubectl create namespace argocd 
```

### Install ArgoCD to k3d cluster
```shell
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

### Get initial pass for web 
```shell
kubectl -n argocd get secrets argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```
### Forward port to localhost and login 
```shell
kubectl port-forward svc/argocd-server -n argocd 8080:443
```
Now you can login to ArgoCD with login admin 
