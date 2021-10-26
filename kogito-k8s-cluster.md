- Test Env
  - k8s cluster with master node on t3.medium
  - 2 worker nodes on t2.2xlarge
  - ran out of CPUs to increase more replicas
- 1 replica of quarkus and 3 replica of mongo
	```
	 curl http://localhost:9090/benchmark/simple/120/60
	{
	"noOfExecutions" : 135216,
	"noOfFailures" : 0,
	"minResponseTime" : {
		"index" : 23131,
		"responseTime" : 4
	},
	"maxResponseTime" : {
		"index" : 134940,
		"responseTime" : 3668
	},
	"averageResponseTime" : 52,
	"percentile95" : 94,
	"percentile99" : 195,
	"totalTimeMillis" : 7127474,
	"elapsedTimeMillis" : 120029,
	"requestsPerSecond" : 1126.0
	}
	```
	```
	[ec2-user@ip-172-20-48-244 test-clients]$ curl http://localhost:9090/benchmark/simple/120/60
	{
	"noOfExecutions" : 130716,
	"noOfFailures" : 0,
	"minResponseTime" : {
		"index" : 19074,
		"responseTime" : 3
	},
	"maxResponseTime" : {
		"index" : 72169,
		"responseTime" : 6229
	},
	"averageResponseTime" : 54,
	"percentile95" : 94,
	"percentile99" : 328,
	"totalTimeMillis" : 7132593,
	"elapsedTimeMillis" : 120012,
	"requestsPerSecond" : 1089.0
	}
	```	
 - 3 replicas of quarkus and 3 replicas of mongo
```
curl http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 144686,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 63114,
    "responseTime" : 3
  },
  "maxResponseTime" : {
    "index" : 117325,
    "responseTime" : 980
  },
  "averageResponseTime" : 49,
  "percentile95" : 95,
  "percentile99" : 110,
  "totalTimeMillis" : 7127634,
  "elapsedTimeMillis" : 120062,
  "requestsPerSecond" : 1205.0
}
```
-3 replicas of app and mongo CPU request - 4 memory - 4 Gi each 
```
curl http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 287307,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 5876,
    "responseTime" : 3
  },
  "maxResponseTime" : {
    "index" : 51900,
    "responseTime" : 12954
  },
  "averageResponseTime" : 24,
  "percentile95" : 47,
  "percentile99" : 67,
  "totalTimeMillis" : 7052053,
  "elapsedTimeMillis" : 120024,
  "requestsPerSecond" : 2393.0
}
```
-3 replicas of app and mongo CPU request - 4 memory - 8 Gi each
```
[ec2-user@ip-172-20-48-244 ~]$ curl http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 280697,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 244135,
    "responseTime" : 2
  },
  "maxResponseTime" : {
    "index" : 137835,
    "responseTime" : 15978
  },
  "averageResponseTime" : 25,
  "percentile95" : 43,
  "percentile99" : 71,
  "totalTimeMillis" : 7110086,
  "elapsedTimeMillis" : 123072,
  "requestsPerSecond" : 2280.0
}
```
- 3 replicas of app and mongo CPU request - 6 memory - 8 Gi each
```
[ec2-user@ip-172-20-48-244 ~]$ curl http://localhost:9090/benchmark/simple/120/60
{
  "noOfExecutions" : 290400,
  "noOfFailures" : 0,
  "minResponseTime" : {
    "index" : 1440,
    "responseTime" : 3
  },
  "maxResponseTime" : {
    "index" : 65429,
    "responseTime" : 16574
  },
  "averageResponseTime" : 24,
  "percentile95" : 28,
  "percentile99" : 59,
  "totalTimeMillis" : 7052251,
  "elapsedTimeMillis" : 120017,
  "requestsPerSecond" : 2419.0
}
```

 - RBAC configuration Mongo user
	```
    {
		"_id" : "admin.mongoadmin",
		"userId" : UUID("6785a3db-c047-4810-863a-f02873251329"),
		"user" : "mongoadmin",
		"db" : "admin",
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
		],
		"mechanisms" : [
			"SCRAM-SHA-256"
		]
	}
    ```