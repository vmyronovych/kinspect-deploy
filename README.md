# kinspect-deploy

This repository contains the Kubernetes deployment and CI/CD setup for the **Kinspect API**.

## Prerequisites

- Create k8s secret for docker credentials in a namespace you are going to run your workflows

Set correct values for params `--docker-username` and `--docker-password`. For `--docker-password` you can generate token on docker hub instead of using your login password.

```bash
kubectl create secret -n argo-evetns docker-registry docker-registry-creds \
   --docker-server=https://index.docker.io/v1/ \
   --docker-username=xxxx --docker-password=yyyy
```

- Create k8s secret for ghithub access

Set correct values for params `--from-literal=token=`. You can generate the token on GitHub in your account settings

```bash
kubectl create secret -n argo-events generic github-token-secret --from-literal=token=xxxx
```

- Install Argo Events

```bash
kubectl create namespace argo-events
kubectl apply -f https://raw.githubusercontent.com/argoproj/argo-events/stable/manifests/install.yaml
# Install with a validating admission controller
kubectl apply -f https://raw.githubusercontent.com/argoproj/argo-events/stable/manifests/install-validating-webhook.yaml
kubectl apply -n argo-events -f https://raw.githubusercontent.com/argoproj/argo-events/stable/examples/eventbus/native.yaml

```

## Install ci into k8s

```bash
kubectl apply -f ./ci-install.yaml
```