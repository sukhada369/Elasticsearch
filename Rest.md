# REST API for ES

**SYNTAX**

- curl -X<REST Verb> <Node>:<Port>/<Index>/<Type>/<ID>

**Check Health of Cluster**
- curl 'localhost:9200/_cat/health?v'

**Check Nodes**
- curl 'localhost:9200/_cat/nodes?v'

**Check Indices in ES Cluster**
- curl 'localhost:9200/_cat/indices?v'

**Create an Index**
- curl -XPUT 'localhost:9200/customer?pretty'

**Add data to Index**
Input:

- curl -XPUT 'localhost:9200/customer/external/1?pretty' -d '
{
  "name": "John Doe"
}'

Output:

- curl -XPUT 'localhost:9200/customer/external/1?pretty' -d '
{
  "name": "John Doe"
}'
{
  "_index" : "customer",
  "_type" : "external",
  "_id" : "1",
  "_version" : 1,
  "created" : true
}


**Delete an Index**
- curl -XDELETE 'localhost:9200/customer?pretty'

**Replacing Data**

- curl -XPUT 'localhost:9200/customer/external/1?pretty' -d '
{
  "name": "John Doe"
}'

- curl -XPUT 'localhost:9200/customer/external/1?pretty' -d '
{
  "name": "Jane Doe"
}'

- curl -XPUT 'localhost:9200/customer/external/2?pretty' -d '
{
  "name": "Jane Doe"
}'
