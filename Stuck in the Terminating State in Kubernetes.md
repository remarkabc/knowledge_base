# Stuck in the Terminating State in Kubernetes
```shell
kubectl api-resources --verbs=list --namespaced=true -o name \
| xargs -n 1 kubectl get --ignore-not-found --show-kind -n ${NAMESPACE}
kubectl path crd/kustomizations.kustomize.toolkit.fluxcd.io -p '{"metadata":{"finalizers": [] }}' --type=merge
```
