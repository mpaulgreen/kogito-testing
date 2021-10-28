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
