
# octant

```sh
# ssh -L 7777:localhost:7777 sks.hs.vc
curl -sOL https://github.com/vmware-tanzu/octant/releases/download/v0.9.1/octant_0.9.1_Linux-64bit.rpm
sudo yum localinstall -y octant_0.9.1_Linux-64bit.rpm
rm octant_0.9.1_Linux-64bit.rpm
OCTANT_DISABLE_OPEN_BROWSER=1 octant
```

# argocd binary

```sh
curl -sL https://github.com/argoproj/argo-cd/releases/download/v1.3.0/argocd-linux-amd64 -o argocd
chmod +x argocd
sudo mv argocd /usr/local/bin/argocd
```

kubectl autocompletion

```sh
source <(kubectl completion bash)
```


# kustomize

MacOS

```sh
brew install kustomize
```

linux

```sh
curl -s https://api.github.com/repos/kubernetes-sigs/kustomize/releases |\
    grep browser_download |\
    grep download/kustomize |\
    grep -m 1 linux |\
    cut -d '"' -f 4 |\
    xargs curl -O -L && \
    tar xzf ./kustomize_v*_linux_amd64.tar.gz && \
    mv ./kustomize /usr/local/bin/kustomize && \
    rm kustomize_*_linux_amd64.tar.gz
```

# kubectl

```sh
# amazon linux
yum install -y bash-completion

source <(kubectl completion bash) # setup autocomplete in bash into the current shell, bash-completion package should be installed first.
#echo "source <(kubectl completion bash)" >> ~/.bashrc
alias k=kubectl
complete -F __start_kubectl k
# reload the shell
```

# kail

https://github.com/boz/kail

```sh
curl -sOL https://github.com/boz/kail/releases/download/v0.12.0/kail_0.12.0_linux_amd64.tar.gz
tar zxf kail_0.12.0_linux_amd64.tar.gz
rm -f kail_0.12.0_linux_amd64.tar.gz
sudo mv kail /usr/local/bin/kail
```


# stern

```sh
curl -sLO https://github.com/wercker/stern/releases/download/1.11.0/stern_linux_amd64
mv stern_linux_amd64 stern
chmod +x ./stern
mv stern /usr/local/bin/stern
```
