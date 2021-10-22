- Machine Spec - 8 vCPUs, 32 GM RAM (On-Premise Testing)

- 1st Run
```
curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 261867,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 66840,
    "responseTime" : 3
  },
  "maxResponseTime" : {
    "index" : 184455,
    "responseTime" : 684
  },
  "averageResponseTime" : 26,
  "percentile95" : 60,
  "percentile99" : 110,
  "totalTimeMillis" : 7064594,
  "elapsedTimeMillis" : 120020,
  "requestsPerSecond" : 2181.0
}

```

- 2nd Run
```
ubuntu@ip-10-0-0-223:~/kogito-benchmark/test-apps/process-quarkus-example$
ubuntu@ip-10-0-0-223:~/kogito-benchmark/test-apps/process-quarkus-example$ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 292718,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 764,
    "responseTime" : 1
  },
  "maxResponseTime" : {
    "index" : 289072,
    "responseTime" : 3064
  },
  "averageResponseTime" : 24,
  "percentile95" : 42,
  "percentile99" : 59,
  "totalTimeMillis" : 7050824,
  "elapsedTimeMillis" : 120012,
  "requestsPerSecond" : 2439.0
}
```
- Mongo DB  basic commands
```
show dbs
use kogito_quarkus
show collections
db.demo.simpleHT.createIndex({"id":1})
db.demo.simpleHT.count()
db.demo.simpleHT.remove({})
db.demo.simpleHT.getIndexes()
```

- application.properties for mongo db
```
quarkus.profile=mongo
quarkus.vertx.worker-pool-size=100
quarkus.mongodb.min-pool-size=100
quarkus.mongodb.max-pool-size=100
kogito.persistence.type=mongodb

//following properties needs to be investigated to fine tune CAP (current C=0 and P=5)
quarkus.mongodb.write-concern.safe=false
quarkus.mongodb.write-concern.journal=false
quarkus.mongodb."mongo-client-configs".write-concern.journal=false
quarkus.mongodb."mongo-client-configs".write-concern.safe=false

```