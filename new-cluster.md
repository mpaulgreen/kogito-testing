Hi, OCP cluster is available at:
https://oauth-openshift.apps.kogito-ocp.dgx5.p1.openshiftapps.com/oauth/authorize?client_id=console&redirect_uri=https%3A%2F%2Fconsole-openshift-console.apps.kogito-ocp.dgx5.p1.openshiftapps.com%2Fauth%2Fcallback&response_type=code&scope=user%3Afull&state=d8b88b66

Login command w/ credentials:
oc login https://api.kogito-ocp.dgx5.p1.openshiftapps.com:6443 --username cluster-admin --password 4m9ES-K6yWi-AHF3o-oMysP





kogito-sharded-mongo-mongos-0.kogito-sharded-mongo-svc.mongodb.svc.cluster.local,kogito-sharded-mongo-mongos-1.kogito-sharded-mongo-svc.mongodb.svc.cluster.local:27017/admin?ssl=false


var watchCursor = db.kogitoprocessinstancesevents.watch();
while (!watchCursor.isExhausted()){
    while (watchCursor.hasNext()){
        printjson(watchCursor.next());
    }
}