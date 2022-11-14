# auto-pilot

## Description

This repo uses [ArgoCD's Auto Pilot](https://argocd-autopilot.readthedocs.io/en/stable/Getting-Started/) to boot strap a Kubernetes cluster.

## Deployent

To boot strap a Kubernetes cluster run this command:

```
export GIT_TOKEN=xxxx
export GIT_REPO=https://github.com/polinchw/auto-pilot

argocd-autopilot repo bootstrap --recover
```

## Apps

The applications in this ArgoCD application set will be installed automatically.

+ [cluster-addons](https://github.com/polinchw/cluster-addons) (This will use the values-dev.yaml durning the installation.)
+ [hello-github-webhook](https://github.com/polinchw/hello-github-webhook)

### Rollback 

#### cluster-addons

If you want to roll back the cluster-addons to a previous commit you 
need to change the ref in the kustomization.yaml.   This is an example.

```
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization
resources:
- github.com/polinchw/cluster-addons/overlays/dev?ref=someprevioushashtagorbranch
```

#### hello-github-webhook

To roll back the hello-github-webhook to a previous release you need to change the config_dir.json.  This is an example:

```
{
  "appName": "hello-github-webhook",
  "userGivenName": "hello-github-webhook",
  "destNamespace": "default",
  "destServer": "https://kubernetes.default.svc",
  "srcPath": "hello-github-webhook",
  "srcRepoURL": "https://github.com/polinchw/hello-github-webhook-cd.git",
  "srcTargetRevision": "previous-hash-tag-or-branch-goes-here",
  "labels": null,
  "annotations": null,
  "exclude": "",
  "include": ""
}
```