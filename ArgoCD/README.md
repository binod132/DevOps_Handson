Handson 2
In this handson you will learn how to install ArgoCD on Minikube and Access ArgoCD on a Web browser.
Pre-requisite:
Minikube running
Docker installed and logged in
Run minikube on terminal: minikube start --driver=docker
Check cluster and pods are running: 

Install ArgoCD on minikube
1. Create namespace for ArgoCD
    kubectl create ns argocd

2. Install ArgoCd
    ``` kubernetes
    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.5.8/manifests/install.yaml
    ```
3.  Verify Installation is done: makesure all Pods status are running.
    ```
    kubectl get all -n argocd
    ```
4. Access ArgoCD on web 
    ```
    kubectl port-forward svc/argocd-server -n argocd 8080:443
    ```
5. Get credential for ArgoCD logdin
    ```
    User: admin
    ```
    For password: 
    ```
    kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
    ```

    If not works try using ArgoCD CLI
    Install ArgoCD CLI: 
    ```
    choco install argocd-cli
    ```
    ```
    argocd admin initial-password -n argocd
    ```

To learn ArgoCD 
Note: Use this official Page of ArgoCD
https://argo-cd.readthedocs.io/en/stable/getting_started/
Next things to do
Part 1: Create APP from ArgoCD portal (UI)
Part 2: Connect to Github repo of APP
Part 3: Learn some important features of ArgoCD


