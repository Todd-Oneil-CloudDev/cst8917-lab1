# Database Selection Documentation
## Choice: Azure Cosmos DB (Core SQL API, Serverless Tier)

### Justification
Azure Cosmos DB is the best fit because it natively stores JSON documents, supports flexible schemas, and automatically indexes all fields for fast queries. This makes it ideal for a workload where the data structure may evolve and where low‑latency reads and writes are important. The serverless tier keeps costs low while still providing the performance benefits of a fully managed NoSQL database. For a single, flat JSON object, Cosmos DB provides simplicity without the overhead of a relational system.

### Alternatives Considered
#### Azure Blob Storage
Rejected because Blob Storage is a file store, not a database. It lacks indexing, querying, and partial updates, making it inefficient for structured JSON data. Managing folders/containers for organization adds unnecessary complexity.

#### Azure SQL Database
Rejected because a relational database is excessive for a single JSON document with no relationships or complex schema. SQL is best suited for multi‑table, relational workloads requiring ACID transactions and structured schemas.

#### Azure Table Storage
Considered but rejected due to limited querying capabilities and lack of automatic indexing beyond PartitionKey and RowKey. While inexpensive, it does not provide the flexibility or performance of Cosmos DB for JSON‑based workloads.

#### Cost Considerations
Cosmos DB pricing in Serverless mode is based on Request Units (RUs) consumed, not provisioned throughput. You pay only for the actual operations performed—reads, writes, queries—making it cost‑effective for low‑traffic or lab environments.  
Storage costs are charged per GB of data stored. There is no need to reserve RU/s, and the database scales automatically based on usage, keeping costs predictable and minimal for small workloads.