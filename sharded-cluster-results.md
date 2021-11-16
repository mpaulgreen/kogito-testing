-- sharded on id hash - no data deleted between runs. unique index dropped (created 100 chunks) that was even distributed with ~33 each on each shard
- 3 shards with 3 replicas for each shard and 2 mongos and 3 mongoconfigsrv
- Each shard is cosuming ~ 8Gi of memory (Issue) 
- opsman 3 replicas always consume ~ 7.5Gi Memory
```
/work $ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 255116,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 106269,
    "responseTime" : 3
  },
  "maxResponseTime" : {
    "index" : 14,
    "responseTime" : 3670
  },
  "averageResponseTime" : 27,
  "percentile95" : 86,
  "percentile99" : 105,
  "totalTimeMillis" : 7069571,
  "elapsedTimeMillis" : 120066,
  "requestsPerSecond" : 2124.0

/work $ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 638060,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 240,
    "responseTime" : 2
  },
  "maxResponseTime" : {
    "index" : 63465,
    "responseTime" : 222
  },
  "averageResponseTime" : 10,
  "percentile95" : 40,
  "percentile99" : 74,
  "totalTimeMillis" : 6876015,
  "elapsedTimeMillis" : 120009,
  "requestsPerSecond" : 5316.0

/work $ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 766801,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 49,
    "responseTime" : 2
  },
  "maxResponseTime" : {
    "index" : 727637,
    "responseTime" : 225
  },
  "averageResponseTime" : 8,
  "percentile95" : 20,
  "percentile99" : 49,
  "totalTimeMillis" : 6812482,
  "elapsedTimeMillis" : 120008,
  "requestsPerSecond" : 6389.0

/work $ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 750047,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 1372,
    "responseTime" : 2
  },
  "maxResponseTime" : {
    "index" : 521232,
    "responseTime" : 413
  },
  "averageResponseTime" : 9,
  "percentile95" : 19,
  "percentile99" : 49,
  "totalTimeMillis" : 6823764,
  "elapsedTimeMillis" : 120009,
  "requestsPerSecond" : 6249.0
```


- 6 shards - 100 chunks

```
/work $ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 678001,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 119,
    "responseTime" : 2
  },
  "maxResponseTime" : {
    "index" : 279057,
    "responseTime" : 229
  },
  "averageResponseTime" : 10,
  "percentile95" : 22,
  "percentile99" : 52,
  "totalTimeMillis" : 6856578,
  "elapsedTimeMillis" : 120011,
  "requestsPerSecond" : 5649.0

/work $ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 683304,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 54,
    "responseTime" : 2
  },
  "maxResponseTime" : {
    "index" : 320694,
    "responseTime" : 246
  },
  "averageResponseTime" : 10,
  "percentile95" : 22,
  "percentile99" : 52,
  "totalTimeMillis" : 6852854,
  "elapsedTimeMillis" : 120012,
  "requestsPerSecond" : 5693.0

/work $ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 686324,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 77,
    "responseTime" : 2
  },
  "maxResponseTime" : {
    "index" : 512301,
    "responseTime" : 230
  },
  "averageResponseTime" : 9,
  "percentile95" : 22,
  "percentile99" : 52,
  "totalTimeMillis" : 6852326,
  "elapsedTimeMillis" : 120009,
  "requestsPerSecond" : 5718.0

/work $ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 661324,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 96,
    "responseTime" : 2
  },
  "maxResponseTime" : {
    "index" : 428997,
    "responseTime" : 1393
  },
  "averageResponseTime" : 10,
  "percentile95" : 22,
  "percentile99" : 53,
  "totalTimeMillis" : 6864744,
  "elapsedTimeMillis" : 120011,
  "requestsPerSecond" : 5510.0

/work $ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 670505,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 3382,
    "responseTime" : 2
  },
  "maxResponseTime" : {
    "index" : 250930,
    "responseTime" : 258
  },
  "averageResponseTime" : 10,
  "percentile95" : 21,
  "percentile99" : 52,
  "totalTimeMillis" : 6861111,
  "elapsedTimeMillis" : 120012,
  "requestsPerSecond" : 5586.0
}
```

- HEX Based Chunk Split
- 8 Shards 

```
/work $ curl -X GET http://localhost:9090/benchmark/simple/120/60  (with autosplitter and balancer off)
{
  "noOfExecutions" : 610522,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 3405,
    "responseTime" : 3
  },
  "maxResponseTime" : {
    "index" : 45,
    "responseTime" : 361
  },
  "averageResponseTime" : 11,
  "percentile95" : 25,
  "percentile99" : 54,
  "totalTimeMillis" : 6892191,
  "elapsedTimeMillis" : 120010,
  "requestsPerSecond" : 5087.0

/work $ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 591155,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 231,
    "responseTime" : 2
  },
  "maxResponseTime" : {
    "index" : 131400,
    "responseTime" : 936
  },
  "averageResponseTime" : 11,
  "percentile95" : 26,
  "percentile99" : 57,
  "totalTimeMillis" : 6901434,
  "elapsedTimeMillis" : 120021,
  "requestsPerSecond" : 4925.0

/work $ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 610523,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 43,
    "responseTime" : 2
  },
  "maxResponseTime" : {
    "index" : 20724,
    "responseTime" : 210
  },
  "averageResponseTime" : 11,
  "percentile95" : 26,
  "percentile99" : 56,
  "totalTimeMillis" : 6891415,
  "elapsedTimeMillis" : 120012,
  "requestsPerSecond" : 5087.0


/work $ curl -X GET http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 604852,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 303,
    "responseTime" : 2
  },
  "maxResponseTime" : {
    "index" : 170649,
    "responseTime" : 218
  },
  "averageResponseTime" : 11,
  "percentile95" : 26,
  "percentile99" : 56,
  "totalTimeMillis" : 6894488,
  "elapsedTimeMillis" : 120011,
  "requestsPerSecond" : 5039.0
}/work $
```