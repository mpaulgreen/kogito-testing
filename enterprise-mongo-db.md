- Setting the CRD, mongodb operator and operations manager
```
oc new-project mongodb

oc create -f https://github.com/mongodb/mongodb-enterprise-kubernetes/raw/master/crds.yaml

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

// Steps to create the API Key and Organization. 

oc apply -f sharded-cluster.yaml
```



oc apply -f opsman-configmap.yaml
oc apply -f opsman-secret.yaml


```


mongo --host kogito-sharded-mongo-mongos-0.kogito-sharded-mongo-svc.mongodb.svc.cluster.local --port 27017

