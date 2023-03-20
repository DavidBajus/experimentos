1. preparing PV and PVC   -> redis-data-claim  
(example can be found in kubernetes/volumes folder)


2. install: 
helm install my-redis --set master.persistence.existingClaim=redis-data-claim bitnami/redis

or

helm install acc-redis -f redis_values.yaml redis

