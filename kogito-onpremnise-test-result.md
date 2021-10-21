- Machine Spec - 4 vCPUs, 16 GM RAM (On-Premise Testing)

- ***Results indicate that there is no issue with throughput or response time for kogito process. For persistence, the througput number are very low and response time is very high.***

- Test Run - not persistable process, threads(60), time(120s)

```
ubuntu@ip-10-0-0-180:/opt/fsi-kogito/kogito-benchmark/test-clients/quarkus-client$ curl -X GET http://localhost:9090/benchmark/notPersisted/120/60
{
  "noOfExecutions" : 523177,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 22,
    "responseTime" : 0
  },
  "maxResponseTime" : {
    "index" : 58342,
    "responseTime" : 603
  },
  "averageResponseTime" : 13,
  "percentile95" : 42,
  "percentile99" : 62,
  "totalTimeMillis" : 6935562,
  "elapsedTimeMillis" : 120017,
  "requestsPerSecond" : 4359.0
}

```

- Test Run - not persistable process, threads(60), time(300s)

```
ubuntu@ip-10-0-0-180:/opt/fsi-kogito/kogito-benchmark/test-clients/quarkus-client$ curl -X GET http://localhost:9090/benchmark/notPersisted/300/60
{
  "noOfExecutions" : 1218389,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 38,
    "responseTime" : 0
  },
  "maxResponseTime" : {
    "index" : 549851,
    "responseTime" : 1445
  },
  "averageResponseTime" : 14,
  "percentile95" : 44,
  "percentile99" : 69,
  "totalTimeMillis" : 17388028,
  "elapsedTimeMillis" : 300013,
  "requestsPerSecond" : 4061.0
}

```

- Test Run - Mongo DB persistable process, threads(60), time(120s)

```
ubuntu@ip-10-0-0-180:/opt/fsi-kogito/kogito-benchmark/test-clients/quarkus-client$ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 6714,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 1012,
    "responseTime" : 228
  },
  "maxResponseTime" : {
    "index" : 3873,
    "responseTime" : 3854
  },
  "averageResponseTime" : 1074,
  "percentile95" : 1733,
  "percentile99" : 2266,
  "totalTimeMillis" : 7213405,
  "elapsedTimeMillis" : 120541,
  "requestsPerSecond" : 55.0
}

```
- Test Run - Mongo DB persistable process, threads(60), time(300s)

```
ubuntu@ip-10-0-0-180:/opt/fsi-kogito/kogito-benchmark/test-clients/quarkus-client$ curl -X GET http://localhost:9090/benchmark/simple/300/60
{
  "noOfExecutions" : 15052,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 7561,
    "responseTime" : 461
  },
  "maxResponseTime" : {
    "index" : 13069,
    "responseTime" : 4150
  },
  "averageResponseTime" : 1196,
  "percentile95" : 1885,
  "percentile99" : 2526,
  "totalTimeMillis" : 18007159,
  "elapsedTimeMillis" : 300705,
  "requestsPerSecond" : 50.0
}

```



