# Harbor instalation steps using Helm

Add Harbor Helm repository:
```
helm repo add harbor https://helm.goharbor.io
helm repo update
```

You can download the default values.yaml file.

```
wget https://raw.githubusercontent.com/goharbor/harbor-helm/master/values.yaml
```

Update values.yaml before installation or use our example

install harbor
```
helm install harbor harbor/harbor -f values.yaml -n harbor

helm status harbor
```

# Pre-installation steps
1. Install ingress
2. Install postgreSQL database
3. Install Redis database
4. Prepare PV and PVC for Harbor (20+ GB)



