# gitops-demo
Using argocd for gitops



# tl;dr
```sh
kind create cluster --name demo01
alias k='kubectl --context kind-demo01'

kustomize build argocd/setup | k apply -n argocd -f  -

stern ".*" --all-namespaces --tail 0
# cleanup
kind delete cluster --name demo01
kustomize build argocd/setup | k delete -f  -
```

error
```
argocd argocd-repo-server-69898c566b-k72xb argocd-repo-server time="2020-01-07T00:04:18Z" level=info msg="kustomize build /tmp/https:__github.com_otsuarez_gitops-demo/addons/local" dir= execID=T95Iz
argocd argocd-repo-server-69898c566b-k72xb argocd-repo-server time="2020-01-07T00:04:18Z" level=error msg="`kustomize build /tmp/https:__github.com_otsuarez_gitops-demo/addons/local` failed exit status 1: Error: var '{APP_DOMAIN ~G_v1_ConfigMap {data.domain}}' cannot be mapped to a field in the set of known resources" execID=T95Iz
argocd argocd-repo-server-69898c566b-k72xb argocd-repo-server time="2020-01-07T00:04:18Z" level=error msg="finished unary call with code Unknown" error="`kustomize build /tmp/https:__github.com_otsuarez_gitops-demo/addons/local` failed exit status 1: Error: var '{APP_DOMAIN ~G_v1_ConfigMap {data.domain}}' cannot be mapped to a field in the set of known resources" grpc.code=Unknown grpc.method=GenerateManifest grpc.request.deadline="2020-01-07T00:05:17Z" grpc.service=repository.RepoServerService grpc.start_time="2020-01-07T00:04:17Z" grpc.time_ms=624.536 span.kind=server system=grpc
argocd argocd-application-controller-64889d9f8-42w58 argocd-application-controller time="2020-01-07T00:04:18Z" level=info msg="Normalized app spec: {\"status\":{\"conditions\":[{\"message\":\"rpc error: code = Unknown desc = `kustomize build /tmp/https:__github.com_otsuarez_gitops-demo/addons/local` failed exit status 1: Error: var '{APP_DOMAIN ~G_v1_ConfigMap {data.domain}}' cannot be mapped to a field in the set of known resources\",\"type\":\"ComparisonError\"}]}}" application=addons
```
