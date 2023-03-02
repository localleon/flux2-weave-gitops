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
```