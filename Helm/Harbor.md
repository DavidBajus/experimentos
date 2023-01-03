# Harbor values
expose:

  ingress:

    hosts:

      core: core.harbor.acc

      notary: notary.harbor.acc

    controller: default



## If Harbor is deployed behind the proxy, set it as the URL of proxy

externalURL: https://core.harbor.acc



#The persistence is enabled by default and a default StorageClass

#is needed in the k8s cluster to provision volumes dynamically.

#Specify another StorageClass in the "storageClass" or set "existingClaim"

#if you already have existing persistent volumes to use

//

#For storing images and charts, you can also use "azure", "gcs", "s3",

#"swift" or "oss". Set it in the "imageChartStorage" section

persistence:

  enabled: true

  #Setting it to "keep" to avoid removing PVCs during a helm delete

  #operation. Leaving it empty will delete PVCs after the chart deleted

  #(this does not apply for PVCs that are created for internal database

  #and redis components, i.e. they are never deleted automatically)

  resourcePolicy: "keep"

  persistentVolumeClaim:

    registry:

      # Use the existing PVC which must be created manually before bound,

      # and specify the "subPath" if the PVC is shared with other components

      existingClaim: "harbor-data-claim"



## The initial password of Harbor admin. Change it from portal after launching Harbor

harborAdminPassword: "Harbor12345"



#The secret key used for encryption. Must be a string of 16 chars.

secretKey: "not-a-secure-key"

#If using existingSecretSecretKey, the key must be sercretKey

existingSecretSecretKey: ""



registry:

  credentials:

    username: "harbor_user"

    password: "HarPass123"



trivy:

  #enabled the flag to enable Trivy scanner

  enabled: false



notary:

  enabled: false



database:

  #if external database is used, set "type" to "external"

  #and fill the connection informations in "external" section

  type: external

  external:

    host: "postgres-postgresql"

    port: "5432"

    username: "appUser"

    password: "AppPassword"

    coreDatabase: "app_db"


# Redis

redis:

  #if external Redis is used, set "type" to "external"

  #and fill the connection informations in "external" section

  type: external

  external:

    #support redis, redis+sentinel

    #addr for redis: <host_redis>:<port_redis>

    #addr for redis+sentinel: <host_sentinel1>:<port_sentinel1>,<host_sentinel2>:<port_sentinel2>,<host_sentinel3>:<port_sentinel3>

    addr: "acc-redis-master:6379"

    #The name of the set of Redis instances to monitor, it must be set to support redis+sentinel

    password: "RedisPass123"
