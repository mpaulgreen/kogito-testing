- To create a rosa cluster interractively

```
rosa create cluster --interactive
```

- Output 
```
rosa create cluster --cluster-name mpkogito --multi-az --region ca-central-1 --version 4.9.13 --enable-autoscaling --min-replicas 3 --max-replicas 6 --compute-machine-type c5.4xlarge --machine-cidr 10.0.0.0/16 --service-cidr 172.30.0.0/16 --pod-cidr 10.128.0.0/14 --host-prefix 23 --etcd-encryption --disable-workload-monitoring
```

- To determine when your cluster is Ready, run 
```
rosa describe cluster -c mpkogito
```
- To watch your cluster installation logs, run
```
rosa logs install -c mpkogito --watch
```
- To view a list of clusters and their status, run 
```
rosa list clusters
```

- Once the cluster is installed you will need to add an Identity Provider before you can login into the cluster. See ```rosa create idp --help``` for more information.

- Details Page - https://console.redhat.com/openshift/details/s/23pKXamwI1T9QrEYlw5TkkNwSrQ

- Create ```cluster-admin``` user
```
rosa create admin --cluster=mpkogito
```

- Return output of the above command
```
oc login https://api.mpkogito.c25t.p1.openshiftapps.com:6443 --username cluster-admin --password vCCXJ-SwhQC-HCcZr-ck9QQ
```



   kubectl get secret kogito-mongodb-admin-developer -n mpaul-kogito -o json | jq -r '.data | with_entries(.value |= @base64d)'

   kubectl -n mpaul-kogito exec --stdin --tty kogito-mongodb-0 -- /bin/bash

    kubectl -n mongodb exec --stdin --tty kogito-benchmark-client-645d764d59-slrxg --sh

{
  "connectionString.standard": "mongodb://developer:password@kogito-mongodb-0.kogito-mongodb-svc.mpaul-kogito.svc.cluster.local:27017,kogito-mongodb-1.kogito-mongodb-svc.mpaul-kogito.svc.cluster.local:27017,kogito-mongodb-2.kogito-mongodb-svc.mpaul-kogito.svc.cluster.local:27017/admin?ssl=false",
  "connectionString.standardSrv": "mongodb+srv://developer:password@kogito-mongodb-svc.mpaul-kogito.svc.cluster.local/admin?ssl=false",
  "password": "password",
  "username": "developer"
}

kubectl create secret docker-registry private-reg-cred \
    --docker-server=quay.io \
    --docker-username=mpaulgreen \
    --docker-password=Andromeda@22 \
    --docker-email=mpaul@redhat.com

    db.createUser(
        "user": "mongoadmin",
        "pwd": "mongoadmin",
        "roles" : [
			{
				"role" : "readWriteAnyDatabase",
				"db" : "admin"
			},
			{
				"role" : "root",
				"db" : "admin"
			},
			{
				"role" : "userAdminAnyDatabase",
				"db" : "admin"
			},
			{
				"role" : "dbAdminAnyDatabase",
				"db" : "admin"
			}
		]
    )



db.createUser({ user: "mongoadmin" , pwd: "mongoadmin", roles: ["userAdminAnyDatabase", "dbAdminAnyDatabase", "readWriteAnyDatabase", "root"]})



