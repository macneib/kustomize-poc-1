```
kind create cluster --config=infra/kind-config.yaml
```

```
kubectl create namespace argocd
kubectl apply -n argocd -f infra/argo-cd-install.yaml
```

```
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
```


```
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```


```
argocd login <ARGOCD_SERVER>
```
