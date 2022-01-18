Modify the application to use shard keys. You need to choose a shard key from a collection and split the data using the key's value.
    - It should determnine document distribution among the different shards in a cluster
    - It should be field that exists in every document in the collection and can be indexed or indexed compound field
    - Performs data partitions in a collection
Chossing shard key
    - Must be easily divisible
        - An easliy divisible shard key enables data distribution among shards. If shard keys containe limited number of possible values, then the chunks in shards cannot be split
    - High degree of randomness
        - This ensures that a single shard distributes write operations among the cluster and does not become a bottleneck
    - Target a single shard
        - A shard key must targt a single shard to enable the mongos program to query operation directly from a single mongod instance
    - Use a compound shard key
        - Compute a special purpose shard key or use a compoine shard ket if the existing field in a collection is not an ideal key


- Commands
```
sh.status()
sh.enableSharding('dbName')
sh.shardCollection('dbName.collectionName',{'from.country':1,'from.number':1})
sh.shardCollection('dbName.collectionName',{'fieldName':'hashed'}) # for hashing- only for a single key - looses locality
show dbs
show collections
db.messages.getIndexes()

// Tagging a shard
sh.addShardTag('shardName', 'tagName')
sh.addTagRange('collection with namespace', 'key range', 'tag')
sh.addTagRange("telco.messages',{country : "01"}, {country: "02"}, "theTag")

// move chunk
sh.moveChunk("telco.messages", {country: "01"}, "shard0002")


//Querying the chunks
use config
db.chunks.find.pretty()

use dbName
db.messages.find('from.country':'44','from.number':'13455553').pretty()
```

- Picking a shard key
    - Cant change shard key definition
    - Cant unshard a collection
    - Shard key field value cant be changed
- Pick a shard key with high cardinality
- Choosing a good key
    - Your access pattern
    - Theoritical granularity
    - Actual Granularity
- Hashed Key
- Tag aware sharding
