# Local Registry Image

This repository contains the Dockerfile and Kustomize resources to deploy a private
docker registry on kubernetes with local storage as its backing storage.

# Setup

## Install Kubernetes resources

The following command will create the registry namespace, deployment, service, and
istio virtualservice:

`kubectl apply -k deploy`
