sh.enableSharding("kogito_quarkus");
sh.shardCollection("kogito_quarkus.demo.simpleHT", {"id" : 1});
sh.stopBalancer();
// Simply use a for loop for each digit
for ( var x=0; x < 16; x++ ){
  for( var y=0; y<16; y++ ) {
  // for the innermost loop we will increment by 2 to get 2048 total iterations
  // make this z++ for 4096 - that would give ~30MB chunks based on the original figures
    for ( var z=0; z<16; z+=2 ) {
    // now construct the GUID with zeroes for padding - handily the toString method takes an argument to specify the base
        var prefix = "" + x.toString(16) + y.toString(16) + z.toString(16) + "00000000000000000000000000000";
        // finally, use the split command to create the appropriate chunk
        db.adminCommand( { split : "kogito_quarkus.demo.simpleHT" , middle : { id : prefix } } );
    }
  }
}

// after 2049 chunks are created

sh.startBalancer();

db.demo.simpleHT.dropIndex({"id":1})
db.adminCommand( { setFeatureCompatibilityVersion: "4.2" } )

sh.enableSharding("kogito");
- Mongo DB  basic commands
```
show dbs
use kogito_quarkus
show collections
db.demo.simpleHT.createIndex({"id":1})
db.demo.simpleHT.count()
db.demo.simpleHT.remove({})
db.demo.simpleHT.getIndexes()
db.demo.simpleHT.insert({"id":1})
db.demo.simpleHT.drop()

-- hashed shards
> from admin db

sh.enableSharding('kogito_quarkus')

db.runCommand({ shardCollection: "kogito_quarkus.demo.simpleHT", key: {"id":"hashed"}, numInitialChunks: 100});

db.runCommand({ shardCollection: "kogito.demo.simpleHT", key: {"id":"hashed"}, numInitialChunks: 100});

db.createUser({ user: "mongoadmin" , pwd: "mongoadmin", roles: ["userAdminAnyDatabase", "dbAdminAnyDatabase", "readWriteAnyDatabase", "root"]})

db.runCommand({createRole:"listDatabases",privileges:[{resource:{cluster:true}, actions:["listDatabases"]}],roles:[]})
db.createUser({"user" : "mongoadmin", pwd:"mongoadmin","roles" : [ { "role" : "listDatabases", "db" : "admin"}, { "role" : "read", "db" : "database_where_collections_are"},{"role": "read", "db" : "local"}]})

curl -X GET http://localhost:9090/benchmark/simple/120/60


------



// 8 shard cluster

use kogito_quarkus
sh.enableSharding("kogito_quarkus")
db.demo.simpleHT.ensureIndex({id: 1})
sh.shardCollection("kogito_quarkus.demo.simpleHT",{"id":1})
sh.disableAutoSplit()
sh.stopBalancer()
sh.status()

for ( var x=2; x < 16; x+=2){var prefix = "" + x.toString(16) + "0000000000000000000000000000000";db.adminCommand( { split : "kogito_quarkus.demo.simpleHT" , middle : { id : prefix } } );}

use config
var cursor = db.chunks.find({ ns: 'kogito_quarkus.demo.simpleHT'});
var shardIndex = 0;
cursor.forEach(function(d) { 
    print( "chunk: " + d.min.id ); 
    print( "shardIndex: " + ("kogito-sharded-mongo-"+(shardIndex)) ); 
    // sh.moveChunk("kogito_quarkus.demo.simpleHT", { "id" : d.min.id }, ("kogito-sharded-mongo-"+(shardIndex++)))
});

db.demo.simpleHT.getShardDistribution()


// fixed 4 shard script
use kogito_quarkus
sh.enableSharding("kogito_quarkus")
db.demo.simpleHT.ensureIndex({id: 1})
sh.shardCollection("kogito_quarkus.demo.simpleHT",{"id":1})
sh.disableAutoSplit()
sh.stopBalancer()pre-split-instructions_4_Shards_Testing.txt
sh.status()

for ( var x=4; x < 16; x+=4){var prefix = "" + x.toString(16) + "0000000000000000000000000000000";db.adminCommand( { split : "kogito_quarkus.demo.simpleHT" , middle : { id : prefix } } );}

use config
var cursor = db.chunks.find({ ns: 'kogito_quarkus.demo.simpleHT'});
var shardIndex = 0;
cursor.forEach(function(d) {
 print( "chunk: " + d.min.id );
 print( "shardIndex: " + ("kogito-sharded-mongo-"+(shardIndex)) );
 sh.moveChunk("kogito_quarkus.demo.simpleHT", { "id" : d.min.id }, ("kogito-sharded-mongo-"+(shardIndex)));
 shardIndex = shardIndex + 1;
});


// fixed 8 shard script
use kogito_quarkus
sh.enableSharding("kogito_quarkus")
db.demo.simpleHT.ensureIndex({id: 1})
sh.shardCollection("kogito_quarkus.demo.simpleHT",{"id":1})
sh.disableAutoSplit()
sh.stopBalancer()pre-split-instructions_4_Shards_Testing.txt
sh.status()

for ( var x=2; x < 16; x+=2){var prefix = "" + x.toString(16) + "0000000000000000000000000000000";db.adminCommand( { split : "kogito_quarkus.demo.simpleHT" , middle : { id : prefix } } );}

use config
var cursor = db.chunks.find({ ns: 'kogito_quarkus.demo.simpleHT'});
var shardIndex = 0;
cursor.forEach(function(d) {
 print( "chunk: " + d.min.id );
 print( "shardIndex: " + ("kogito-sharded-mongo-"+(shardIndex)) );
 sh.moveChunk("kogito_quarkus.demo.simpleHT", { "id" : d.min.id }, ("kogito-sharded-mongo-"+(shardIndex)));
 shardIndex = shardIndex + 1;
});