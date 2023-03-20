# for persitent volume create PV and PVC
Example of PV and PVC can be found in kubernetes/volumes folder.

# prepare custom values.yaml
After creating PV and PVC, create a new configuration file (values.yaml) for helm installation

# define default database user, name, and password for PostgreSQL deployment
```
auth:
  enablePostgresUser: true
  postgresPassword: "StrongPassword"
  username: "app1"
  password: "AppPassword"
  database: "app_db"
```

# Set PVC for postgres installation and enable init container for setting up permissions
```
primary:
  persistence:
    enabled: true
    existingClaim: "postgresql-data-claim"

volumePermissions:
  enabled: true
```
    
    
## Deploying PostgreSQL to Kubernetes

Run the helm install command below to deploy PostgreSQL to Kubernetes with the name e.g.:postgresql-dev using the Bitnami Helm chart (bitnami/postgresql):

helm install postgresql-dev -f values.yaml bitnami/postgresql


Now, run the kubectl commands below to check the PostgreSQL pod and pod’s logs. Be sure to change postgresql-dev-0 with your pod.

# Checking pods
kubectl get pods

# Checking logs of pods
kubectl logs postgresql-dev-0


## Connecting to PostgreSQL

Run the below export command to create the POSTGRES_PASSWORD environment variable, which contains the password for the PostgreSQL database (app_db).

```
export POSTGRES_PASSWORD=$(kubectl get secret --namespace default postgresql-dev -o jsonpath="{.data.password}" | base64 --decode)
```

Next, run the kubectl run command below to connect to the PostgreSQL database (app_db).

```
kubectl run postgresql-dev-client --rm --tty -i --restart='Never' --namespace default --image docker.io/bitnami/postgresql:14.1.0-debian-10-r80 --env="PGPASSWORD=$POSTGRES_PASSWORD" \
--command -- psql --host postgresql-dev -U app1 -d app_db -p 5432
```

Lastly, run the following PostgreSQL query to verify your connection to the PostgreSQL database.

# Checking PostgreSQL connection
\conninfo

# Logout from PostgreSQL shell
exit
