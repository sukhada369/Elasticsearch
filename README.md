# Elasticsearch

- Elasticsearch is a highly scalable open-source full-text search and analytics engine
- It allows you to store, search, and analyze big volumes of data quickly and in near real time

**Usecase:**

- You run an online web store where you allow your customers to search for products that you sell. In this case, you can use Elasticsearch to store your entire product catalog and inventory and provide search and autocomplete suggestions for them.
- You want to collect log or transaction data and you want to analyze and mine this data to look for trends, statistics, summarizations, or anomalies. In this case, you can use Logstash (part of the Elasticsearch/Logstash/Kibana stack) to collect, aggregate, and parse your data, and then have Logstash feed this data into Elasticsearch. Once the data is in Elasticsearch, you can run searches and aggregations to mine any information that is of interest to you.
- You run a price alerting platform which allows price-savvy customers to specify a rule like "I am interested in buying a specific electronic gadget and I want to be notified if the price of gadget falls below $X from any vendor within the next month". In this case you can scrape vendor prices, push them into Elasticsearch and use its reverse-search (Percolator) capability to match price movements against customer queries and eventually push the alerts out to the customer once matches are found.
- You have analytics/business-intelligence needs and want to quickly investigate, analyze, visualize, and ask ad-hoc questions on a lot of data (think millions or billions of records). In this case, you can use Elasticsearch to store your data and then use Kibana (part of the Elasticsearch/Logstash/Kibana stack) to build custom dashboards that can visualize aspects of your data that are important to you. Additionally, you can use the Elasticsearch aggregations functionality to perform complex business intelligence queries against your data.

**Key Terminologies:**

**NRT(Near Real Time)**
**Cluster:**

- Collection of one or more nodes (servers) that together holds your entire data and provides federated indexing and search capabilities across all nodes.
- A cluster is identified by a unique name which by default is "elasticsearch".
- This name is important because a node can only be part of a cluster if the node is set up to join the cluster by its name.

- Note:
- Make sure that you don’t reuse the same cluster names in different environments, otherwise you might end up with nodes joining the wrong cluster. For instance you could use logging-dev,logging-stage, and logging-prod for the development, staging, and production clusters.

**Node:**

- Single server that is part of your cluster, stores your data, and participates in the cluster’s indexing and search capabilities.
- Node is identified by a name which by default is a random Marvel character name that is assigned to the node at startup.
- You can configure the name for the node
- This name is important for administration purposes where you want to identify which servers in your network correspond to which nodes in your Elasticsearch cluster.

- A node can be configured to join a specific cluster by the cluster name. By default, each node is set up to join a cluster named elasticsearch which means that if you start up a number of nodes on your network and—assuming they can discover each other—they will all automatically form and join a single cluster named elasticsearch.

- In a single cluster, you can have as many nodes as you want. Furthermore, if there are no other Elasticsearch nodes currently running on your network, starting a single node will by default form a new single-node cluster named elasticsearch.

**Index**

- An index is a collection of documents that have somewhat similar characteristics.
- For example, you can have an index for customer data, another index for a product catalog, and yet another index for order data.
- An index is identified by a name (that must be all lowercase) and this name is used to refer to the index when performing indexing, search, update, and delete operations against the documents in it.

- In a single cluster, you can define as many indexes as you want.

**Type**

- Within an index, you can define one or more types.
- A type is a logical category/partition of your index whose semantics is completely up to you.
- In general, a type is defined for documents that have a set of common fields.
- For example, let’s assume you run a blogging platform and store all your data in a single index.
- In this index, you may define a type for user data, another type for blog data, and yet another type for comments data.

**Document**

- A document is a basic unit of information that can be indexed. For example, you can have a document for a single customer, another document for a single product, and yet another for a single order. This document is expressed in JSON (JavaScript Object Notation) which is an ubiquitous internet data interchange format.

- Within an index/type, you can store as many documents as you want. Note that although a document physically resides in an index, a document actually must be indexed/assigned to a type inside an index.

**Shards and Replicas**



