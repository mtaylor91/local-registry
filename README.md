# R2 Registry Image

This repository contains the Dockerfile and Kustomize resources to deploy a private
docker registry on kubernetes with Cloudflare R2 as it's backing storage.

# Setup

## Install Kubernetes resources

The following command will create the registry namespace, deployment, service, and
istio virtualservice:

`kubectl apply -k deploy`

## Create configuration secret

```
kubectl create secret generic -n registry images-s3 \
    --from-literal=s3-endpoint-url=CLOUDFLARE_R2_ENDPOINT_URL \
    --from-literal=s3-bucket=CLOUDFLARE_R2_BUCKET_NAME \
    --from-literal=access-key=CLOUDFLARE_R2_ACCESS_KEY \
    --from-literal=secret-key=CLOUDFLARE_R2_SECRET_KEY
```

You can obtain `CLOUDFLARE_R2_ENDPOINT_URL`, `CLOUDFLARE_R2_ACCESS_KEY`, and
`CLOUDFLARE_R2_SECRET_KEY` from the Cloudflare dashboard.
