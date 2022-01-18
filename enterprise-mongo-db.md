
- Setting the CRD, mongodb operator and operations manager
```
oc new-project mongodb

- To create the crds and a custom role execute
```
oc create -f https://github.com/mongodb/mongodb-enterprise-kubernetes/raw/master/crds.yaml
```

- The following resources are created
```
customresourcedefinition.apiextensions.k8s.io/mongodb.mongodb.com created
customresourcedefinition.apiextensions.k8s.io/mongodbmulti.mongodb.com created
customresourcedefinition.apiextensions.k8s.io/mongodbusers.mongodb.com created
customresourcedefinition.apiextensions.k8s.io/opsmanagers.mongodb.com created
clusterrole.rbac.authorization.k8s.io/mongodb-enterprise-operator-mongodb-webhook created

```

- To validate the resources created
```
oc get crd | grep mongodb
oc get clusterrole | grep mongodb
```
````


kubectl create secret docker-registry private-reg-cred \
    --docker-server=quay.io \
    --docker-username=mpaul@redhat.com \
    --docker-password=Andromeda@22 \
    --docker-email=mpaul@redhat.com

oc secrets link default private-reg-cred --for=pull

oc create -f https://github.com/mongodb/mongodb-enterprise-kubernetes/raw/master/mongodb-enterprise-openshift.yaml

oc create -f opsman-admin-credentials.yaml

oc apply -f opsman-instance.yaml

oc expose svc ops-manager-svc

oc apply -f opsman-configmap.yaml
oc apply -f opsman-secret.yaml

// Steps to create the API Key and Organization. 
https://github.com/RHEcosystemAppEng/kogito-benchmark/tree/main/sharded-mongodb#setting-up-the-mongo-db-sharded-cluster

oc apply -f sharded-cluster.yaml
```
```
oc port-forward kogito-sharded-mongo-mongos-0 27017:27017
mongosh
db.createUser({ user: "mongoadmin" , pwd: "mongoadmin", roles: ["userAdminAnyDatabase","dbAdminAnyDatabase","readWriteAnyDatabase", "root"]})
```


mongo --host kogito-sharded-mongo-mongos-0.kogito-sharded-mongo-svc.mongodb.svc.cluster.local --port 27017

./mvnw package -Dquarkus.container-image.build=true