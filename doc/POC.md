### Cluster deployment and installation argoCD

1. Cluster creation
```bash
k3d cluster create argo
```
2. Checking containers creation
```bash
docker ps
```
3. Checking cluster components
```bash
kubectl get all -A
```
4. Installation [ArgoCD](https://argo-cd.readthedocs.io/en/stable/#quick-start)
```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
5. Getting access to ArgoCD GUI
```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443&
```
6. Getting password to access ArgoCD GUI
```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"|base64 -d;echo
```
#### Demo of this process:
![Image](.data/argocd_install.gif)
