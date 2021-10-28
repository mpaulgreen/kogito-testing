- All Pods of test app was run on best effot basis as there is identified memory leak issue
- 20 repicas of test app pods 
- Min and max db connection of 10
- worker pool size of 10
- Stateful set of mongodb (3 rs) - Qos 
  - mongod container - cpu 6, memory 12 Gi
  - mongodb-agent conatiner - cpu 2 memory 2Gi
- quarkus bench mark app
  - worker pool of 100
- Test executed with kogito bechmark as a pod and from its tty terminals to avoid network latency
```
/work $ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 1005924,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 257,
    "responseTime" : 1
  },
  "maxResponseTime" : {
    "index" : 977751,
    "responseTime" : 3705
  },
  "averageResponseTime" : 6,
  "percentile95" : 12,
  "percentile99" : 44,
  "totalTimeMillis" : 6745910,
  "elapsedTimeMillis" : 122735,
  "requestsPerSecond" : 8195.0
/work $

/work $ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 1061696,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 36292,
    "responseTime" : 1
  },
  "maxResponseTime" : {
    "index" : 23,
    "responseTime" : 1777
  },
  "averageResponseTime" : 6,
  "percentile95" : 18,
  "percentile99" : 54,
  "totalTimeMillis" : 6650993,
  "elapsedTimeMillis" : 120039,
  "requestsPerSecond" : 8844.0
}/work $


/work $ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 1188953,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 175,
    "responseTime" : 1
  },
  "maxResponseTime" : {
    "index" : 639485,
    "responseTime" : 2073
  },
  "averageResponseTime" : 5,
  "percentile95" : 14,
  "percentile99" : 47,
  "totalTimeMillis" : 6576357,
  "elapsedTimeMillis" : 120003,
  "requestsPerSecond" : 9907.0

```


- Legacy Results


- Executed within the cluster
- 20 replicas
- 10 Connection pool
- 10 worker pool
- 200 worker pool of test client

```
/work $ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 433374,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 1705,
    "responseTime" : 1
  },
  "maxResponseTime" : {
    "index" : 159833,
    "responseTime" : 852
  },
  "averageResponseTime" : 16,
  "percentile95" : 84,
  "percentile99" : 89,
  "totalTimeMillis" : 6973894,
  "elapsedTimeMillis" : 120091,
  "requestsPerSecond" : 3608.0
/work $ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 433694,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 94,
    "responseTime" : 1
  },
  "maxResponseTime" : {
    "index" : 193722,
    "responseTime" : 1585
  },
  "averageResponseTime" : 16,
  "percentile95" : 84,
  "percentile99" : 89,
  "totalTimeMillis" : 6973187,
  "elapsedTimeMillis" : 120033,
  "requestsPerSecond" : 3613.0
}
```
- Executed within the cluster
- 20 replicas
- 10 Connection pool
- 10 worker pool
- 400 worker pool of test client


```
/work $ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 438960,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 206,
    "responseTime" : 1
  },
  "maxResponseTime" : {
    "index" : 160156,
    "responseTime" : 2115
  },
  "averageResponseTime" : 15,
  "percentile95" : 83,
  "percentile99" : 88,
  "totalTimeMillis" : 6973177,
  "elapsedTimeMillis" : 120080,
  "requestsPerSecond" : 3655.0
```

- Executed within the cluster
- 20 replicas
- 20 Connection pool
- 20 worker pool
- 400 worker pool of test client




```

/work $ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 421707,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 51844,
    "responseTime" : 1
  },
  "maxResponseTime" : {
    "index" : 15,
    "responseTime" : 822
  },
  "averageResponseTime" : 16,
  "percentile95" : 82,
  "percentile99" : 88,
  "totalTimeMillis" : 6987678,
  "elapsedTimeMillis" : 120061,
  "requestsPerSecond" : 3512.0
}
```

- Executed within the cluster
- 40 replicas
- 10 Connection pool
- 10 worker pool
- 400 worker pool of test client

```
/work $ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 402586,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 156284,
    "responseTime" : 1
  },
  "maxResponseTime" : {
    "index" : 52,
    "responseTime" : 1291
  },
  "averageResponseTime" : 17,
  "percentile95" : 78,
  "percentile99" : 86,
  "totalTimeMillis" : 6993913,
  "elapsedTimeMillis" : 120013,
  "requestsPerSecond" : 3354.0
}

/work $ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 429717,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 284,
    "responseTime" : 1
  },
  "maxResponseTime" : {
    "index" : 429710,
    "responseTime" : 395
  },
  "averageResponseTime" : 16,
  "percentile95" : 82,
  "percentile99" : 89,
  "totalTimeMillis" : 6991259,
  "elapsedTimeMillis" : 120136,
  "requestsPerSecond" : 3576.0
}
```

- Executed within the cluster
- 80 replicas
- 1 Connection pool
- 1 worker pool
- 100 worker pool of test client

```
{
  "noOfExecutions" : 416480,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 64233,
    "responseTime" : 1
  },
  "maxResponseTime" : {
    "index" : 300360,
    "responseTime" : 302
  },
  "averageResponseTime" : 16,
  "percentile95" : 78,
  "percentile99" : 86,
  "totalTimeMillis" : 6985804,
  "elapsedTimeMillis" : 120034,
  "requestsPerSecond" : 3469.0
```
