# deploy nginx ingress
To deploy nginx ingress run kubectl apply -f deploy_nginx_ingress.yaml

# Or find helm chart on web :)

# example with simple ingres

Create a deployment and expose it as a serivce. 
#This service will be ClusterIP and we'll expose this service via the Ingress. Run simple_ingress file :)

```
kubectl create deployment hello-world-service-single --image=gcr.io/google-samples/hello-app:1.0

kubectl expose deployment hello-world-service-single --port=80 --target-port=8080 --type=ClusterIP
```

# Tip for path base ingress rule
Our paths are routing to their correct services, if we specify a host header or use a DNS name to access the ingress. That's how the rule will route the request.
curl http://$INGRESSIP/red  --header 'Host: path.example.com'
curl http://$INGRESSIP/blue --header 'Host: path.example.com'