# auto-pilot

## Description

This repo uses [ArgoCD's Auto Pilot](https://argocd-autopilot.readthedocs.io/en/stable/Getting-Started/) to boot strap a Kubernetes cluster.

## Deployent

To boot strap a Kubernetes cluster run this command:

```
argocd-autopilot repo bootstrap --recover
```

## Apps

The applications in the ArgoCD Application set will be installed.

+[cluster-addons](https://github.com/polinchw/cluster-addons/tree/dev)