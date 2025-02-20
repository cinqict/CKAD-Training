# CKAD-Training
CKAD-Training

# Requirements:
- docker/podman
- kind (https://kind.sigs.k8s.io/)
- kubectl (https://kubernetes.io/docs/tasks/tools/)
- freelens (https://github.com/freelensapp/freelens/releases/tag/v1.0.0)
- lens (https://k8slens.dev/)

Git clone this repo:
- git clone https://github.com/cinqict/CKAD-Training.git

# Setup Kind Cluster
- kind create cluster --config=config.yaml
  * Setups a kind k8s cluster with 1 system node and 2 worker nodes
  * System node has port 80 and 443 mapped. this is done for the ingress controler
  * Nodes have a label called "tier" to use in nodeselector definitions
- kind get clusters
- kind get kubeconfig --name ckad-cluster

To Delete the cluster run:
- kind delete cluster --name ckad-cluster


# Deploy ingress controller to setup http/https connections using localhost:
- kubectl apply -f deploy-ingress-nginx.yaml

# Deploy demo app welke de ingress gebruikt:
- kubectl apply -f demo-ingress.yaml
- using your browser connect to http(s)://localhost/foo and http(s)://localhost/bar
