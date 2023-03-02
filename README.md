# flux2-weave-gitops

Bootstrap Flux2 Cluster
```
flux bootstrap github \
  --owner=$GITHUB_USER \
  --repository=flux2-weave-gitops \
  --branch=main \
  --path=./clusters/my-cluster \
  --personal
```

Install the Weaveworks Gitops CLI
```
curl --silent --location "https://github.com/weaveworks/weave-gitops/releases/download/v0.18.0/gitops-$(uname)-$(uname -m).tar.gz" | tar xz -C /tmp
sudo mv /tmp/gitops /usr/local/bin
gitops version
```

```
export PASSWORD=""
gitops create dashboard ww-gitops \
  --password=$PASSWORD \
  --export > ./clusters/my-cluster/weave-gitops-dashboard.yaml
git add -A && git commit -m "Add Weave GitOps Dashboard"
git push
```

Access to UI of WeaveGitOps 
```
kubectl port-forward svc/ww-gitops-weave-gitops -n flux-system 9001:9001
```