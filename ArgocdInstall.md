1. Install Argo CD

kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml


2. Port Forwarding

kubectl port-forward svc/argocd-server -n argocd 8080:443


3. Install Argocd

$version = (Invoke-RestMethod https://api.github.com/repos/argoproj/argo-cd/releases/latest).tag_name
$url = "https://github.com/argoproj/argo-cd/releases/download/" + $version + "/argocd-windows-amd64.exe"
$output = "argocd.exe"

Invoke-WebRequest -Uri $url -OutFile $output


4. Login 

Default Username: admin

argocd admin initial-password -n argocd

Delete secret argocd-initial-admin-secret from Argo CD namespace once the password is changed.



