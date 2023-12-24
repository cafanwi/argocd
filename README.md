## 1. Install ArgoCD
Installation Link: [ArgoCD](https://argo-cd.readthedocs.io/en/stable/getting_started/)

### Create Namespace

```sh
kubectl create ns argocd
```

### Get the helm chart and Install Argo cd

```sh
curl https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml > cafanwi-argo.yaml
```

### Apply the file

```sh
kubectl -n argocd apply -f cafanwi-argo.yaml
kubectl -n argocd get all
```

### Port-forward if you're using local host

```sh
kubectl -n argocd port-forward service/argocd-server  8080:443
```

### Get the AgroCd secret

```yaml
kubectl -n argocd get secret
kubectl -n argocd get secret argocd-initial-admin-secret -o yaml | grep -i pass
```

  password: aasdSHDFJHdjejjfkeje==
        f:password: {}

### Decode the secret and 

```sh
echo aasdSHDFJHdjejjfkeje== | base64 -d 
```

4Q-RKESDF5HDSF1

### login Argo UI
username: admin
password: 4Q-RKESDF5HDSF1

## 2. Create the directories in VsCode

```sh
mkdir cafanwii-argocd
cd cafanwii-argocd
```

### Create two directories inside the cafanwii-argocd directory

1. argo-application   --> will contain the argocd control files
2. wordpress --> will be used as a test deployment

```sh
cd cafanwii-argocd
mkdir argo-application
mkdir wordpress
```

### Add the yamk manifests in the directories

See the directories for the added manifests.

### Apply the directories to the kubernetes cluster

```yaml
kubectl apply -f argo-application/
```

## 3. Setup the Github project
Create a Github project. Im using: https://github.com/cafanwi/argocd.git

```sh
git config --global user.name "cafanwi"
git config --global user.email macazzzzzzzzzz@gmail.com
```

```sh
git init
git remote add origin https://github.com/cafanwi/argocd.git
```

### Create a Girhub Personal access token

xxxxxxxx

### setup the git Repo
Click: Settings --> Repositories --> connect VIA HTTPS 

- under username, enter your Github username
- underpassword, enter the access token from Github

---

https://www.arthurkoziel.com/setting-up-argocd-with-helm/

<!-- 
kubectl -n wordpress create secret generic wordpress-secret --from-literal password=password123 --from-literal username=collins --dry-run=client -o yaml  -->


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