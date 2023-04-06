# cluster-addons

## Description

This application is used to deploy a set of 3rd party helm charts 
with ArgoCD Autopilot.

## Deploy Pinned Version

To point to a pinned version of cluster-addons set the **revision** 
and **targetRevision** to a release branch or tag in the application-set.yaml.  The application-set.yaml overrides the file in the cluster-addons repo.