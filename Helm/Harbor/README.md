# Harbor instalation steps using Helm

//Add Harbor Helm repository:
helm repo add harbor https://helm.goharbor.io
helm repo update

//You can download the default values.yaml file.
wget https://raw.githubusercontent.com/goharbor/harbor-helm/master/values.yaml
vim values.yaml
helm install harbor harbor/harbor -f values.yaml -n harbor

helm status harbor


//Grant access to all authenticated users anyone SCC:
oc adm policy add-scc-to-group anyuid system:authenticated








