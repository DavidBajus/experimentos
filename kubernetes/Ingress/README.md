# Setting Up An Ingress Controller

Create a kind cluster with extraPortMappings and node-labels:
 - extraPortMappings allow the local host to make requests to the Ingress controller over ports 80/443;
 - node-labels only allow the ingress controller to run on a specific node(s) matching the label selector.

# NGINX ingress controller 

See file ClusterCongif.yaml

//Create a cluster with the new configuration.
kind create cluster --config newConfig.yaml

//Apply the ingress NGINX controller with the following command:
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml

# Deploy a Service Locally

//should it be here????
