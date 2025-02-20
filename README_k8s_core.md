# Kubernetes core (2 hours)

## Main Goal

The basics of Kubernetes is a steep learning path. This course is ment to guide you through this first part, learn the basics and learn it right. The goal is to enable you to make the next steps yourself.

## Agenda

- What & why Kubernetes
- Pods
- Deployment
- Services
- (optional: Namespaces, ConfigMaps, Volumes)

## Course material

https://gitlab.com/cinqict-devops/course-k8s-2d

## Labs

There is not much time, so the most part will be theory. However, you learn k8s by doing. There are some labs which you can do and I encourage you to experiment and extend these labs.

### Prerequisites

Willen jullie het volgende installeren:

- `kubectl`
  
minstens 1 van deze:
- `kind` (most simple and fast way to create a minimal k8s cluster)
- `az cli` (if you have an CINQ Azure account, you can create compleet k8s cluster with AKS)

### Infra

Setup a k8s cluster.

### Kind

```shell
kind create cluster

kubectl get pods --all-namespaces



kind delete cluster

```

### Azure infra

```shell
az login
az account set --subscription "CINQ ICT"

RESOURCE_GROUP=rg-ericcornet-devops

# Takes up to 5 minutes...
az aks create \
  --resource-group $RESOURCE_GROUP \
  --name k8s-fundamentals \
  --node-count 2 \
  --node-vm-size Standard_DS2_v2 \
  --generate-ssh-keys

# Get your kubeconfig (connection settings stored in $HOME/.kube/config) 
az aks get-credentials --resource-group $RESOURCE_GROUP --name k8s-fundamentals

kubectl get pods --all-namespaces


# Cleanup
az aks delete \
  --resource-group $RESOURCE_GROUP \
  --name k8s-fundamentals \
  --yes --no-wait

# Check 
az aks list --resource-group $RESOURCE_GROUP

```



