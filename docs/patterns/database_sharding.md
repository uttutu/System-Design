Database Sharding
Overview

Database sharding is a horizontal partitioning technique used to improve the scalability, performance, and availability of large databases.
In sharding, data is split across multiple independent databases (called shards) — each holding a subset of the data.
This approach allows systems to handle larger datasets and higher throughput by distributing load instead of relying on a single database instance.

Why Sharding Is Needed

As systems scale, a single database may hit its limits in:

💾 Storage capacity – the dataset becomes too large to fit on one node.

⚙️ Throughput – read/write operations exceed what one server can handle.

🕓 Latency – performance degrades due to large indexes or I/O bottlenecks.

🧩 Maintenance – backups, migrations, and schema changes become slow.

Sharding helps by splitting data horizontally, enabling parallelism and scaling out linearly with the number of shards.

Key Concepts
Concept	Description
Shard	A physical database that holds a subset of data.
Shard Key	The attribute used to determine which shard a record belongs to (e.g., user_id, region).
Shard Map / Routing Layer	Service or logic responsible for directing queries to the correct shard.
Resharding	The process of redistributing data when shards are added, removed, or rebalanced.
Sharding Strategies
1. Range-Based Sharding

Data is divided based on value ranges of a shard key (e.g., users 1–1M in shard A, 1M–2M in shard B).

✅ Pros: Easy to implement; efficient range queries.

⚠️ Cons: Risk of hotspots if data is unevenly distributed.

2. Hash-Based Sharding

A hash function is applied to the shard key to evenly distribute data across shards.

✅ Pros: Even data distribution; good for write-heavy workloads.

⚠️ Cons: Range queries become difficult.

3. Directory-Based Sharding

A lookup table maintains mappings between keys and shards.

✅ Pros: Maximum flexibility for data placement.

⚠️ Cons: Directory can become a bottleneck or single point of failure.

4. Geo-Sharding (Regional Sharding)

Data is partitioned based on user geography or region.

✅ Pros: Reduces latency and complies with data residency requirements.

⚠️ Cons: Complex failover and inter-region queries.

Sharding Architecture

A typical sharded setup involves:

Application Layer — Determines the shard key for each query.

Routing Layer / Middleware — Routes requests to the correct shard (e.g., Vitess, Citus, or custom logic).

Shard Databases — Individual instances, each storing a subset of data.

Metadata Store — Maintains the shard map and configuration metadata.

Challenges in Sharding

🔄 Rebalancing: Adding or removing shards requires data migration.

🔍 Cross-Shard Queries: Joins or aggregations across shards are complex and slow.

💥 Transaction Management: Maintaining ACID properties across shards is non-trivial.

📋 Schema Changes: Must be applied consistently across all shards.

🧠 Operational Complexity: Monitoring, backups, and scaling strategies multiply per shard.

Best Practices

Choose a stable shard key that avoids hotspots.

Keep shard boundaries immutable to prevent rebalancing churn.

Use a routing middleware (like ProxySQL, Vitess, or Citus) for query routing.

Automate resharding and monitoring processes.

Maintain metadata consistency and shard maps under version control.

Plan for growth — avoid fixed shard counts that limit scalability.

Real-World Examples

🧱 YouTube / Vitess: Uses sharding to scale MySQL horizontally.

📦 Amazon: Shards by customer or region for high isolation.

💬 Discord: Shards user sessions and messages for performance.

🎵 Spotify: Combines sharding with caching for distributed playlists.

Common Pitfalls

Uneven data distribution due to poor shard key selection.

Ignoring the cost of cross-shard joins and transactions.

Centralized routing logic becoming a bottleneck.

Lack of tooling for shard management and observability.

Sharding vs. Partitioning
Aspect	Sharding	Partitioning
Scope	Distributed across multiple nodes	Within a single database instance
Goal	Scale out horizontally	Improve manageability/performance
Management	Application-level or middleware	Database-level (e.g., PostgreSQL partitions)
Further Reading

Vitess: Scaling MySQL for YouTube

Citus Data Sharding in PostgreSQL

Google Cloud Spanner Architecture

[Designing Data-Intensive Applications – Martin Kleppmann (Chapter on Partitioning)]
