⚡ Caching in System Design

Caching is the practice of storing frequently accessed data in a faster storage layer (like memory) to reduce latency, lower backend load, and improve overall system performance.
It’s one of the most effective optimizations in distributed systems, often delivering order-of-magnitude speed improvements when implemented well.

🚀 Why Caching Matters

As systems scale, backend databases or APIs often become performance bottlenecks due to repetitive reads and high request rates.
Caching helps mitigate this by:

Reducing latency for frequently requested data

Lowering read load on databases and APIs

Improving user experience and throughput

Reducing operational costs for I/O-heavy systems

🧠 Core Concept

A cache is a temporary storage layer that keeps copies of data so future requests can be served faster.

Common Cache Layers:
Layer	Description	Example
Client-side cache	Stored in user’s browser or app memory	Browser cache, mobile app cache
CDN (Edge cache)	Cached static content close to users geographically	Cloudflare, Akamai
Application cache	In-memory cache in the app layer	Guava Cache, Spring Cache
Distributed cache	Shared cache accessible by multiple servers	Redis, Memcached
Database cache	Query or result cache inside the database	MySQL Query Cache, PostgreSQL Cache
⚙️ Cache Strategies
1. Cache-aside (Lazy Loading)

Application first checks the cache; if not found, fetches from DB and stores it.

Most common and flexible strategy.

if key in cache:
    return cache[key]
else:
    data = db.get(key)
    cache.set(key, data)
    return data


✅ Pros: Simple, on-demand caching
❌ Cons: Possible cache misses for first requests

2. Write-through Cache

Data is written to both the cache and the database synchronously.

✅ Pros: Cache always up-to-date
❌ Cons: Slower writes due to dual updates

3. Write-back (Write-behind) Cache

Writes go to the cache first and are asynchronously flushed to the database later.

✅ Pros: Fast writes, reduced DB load
❌ Cons: Risk of data loss if cache fails before persistence

4. Read-through Cache

The cache is in front of the database — it fetches data automatically on a miss.

✅ Pros: Simplifies app logic
❌ Cons: Cache layer becomes more complex

🧩 Cache Invalidation

Cache invalidation ensures that outdated or stale data does not persist in cache.
This is one of the hardest challenges in caching systems.

Common Invalidation Policies
Policy	Description
TTL (Time-to-Live)	Automatically removes cache entries after a duration
Manual Invalidation	Explicitly evict or update cache when data changes
Write Invalidation	Remove/update cache entries during write operations
Event-driven Invalidation	Listen to DB change streams or message queues to invalidate cache

🧠 Rule of thumb: “There are only two hard things in computer science — cache invalidation and naming things.” — Phil Karlton

📊 Eviction Policies

Caches have limited memory, so eviction policies determine which items to remove when full.

Policy	Description	Example Use Case
LRU (Least Recently Used)	Removes least recently accessed item	Most common general-purpose policy
LFU (Least Frequently Used)	Removes least accessed item overall	Analytical or read-heavy workloads
FIFO (First In, First Out)	Removes oldest cached item	Simple or predictable workloads
Random	Randomly removes entries	Low overhead, probabilistic performance
🧮 Cache Placement
Level	Purpose	Example
Client-Side Cache	Reduces network requests	Browser cache, service workers
Edge Cache (CDN)	Decreases latency for static content	Cloudflare, AWS CloudFront
Server-Side Cache	Reduces backend load	Redis, Memcached
Database Cache	Optimizes query performance	Query cache, materialized views
🧱 Cache Consistency Models
Model	Description	Trade-off
Strong Consistency	Cache always reflects the latest data	Expensive and complex
Eventual Consistency	Cache eventually becomes up-to-date	Faster but may serve stale data temporarily
Write-through Consistency	Writes update both DB and cache	Slower writes, reliable reads
⚡ Cache Performance Metrics
Metric	Description
Cache Hit Ratio	% of requests served from cache
Cache Miss Rate	% of requests not found in cache
Eviction Rate	% of entries removed from cache due to capacity
Latency Reduction	Improvement in response time due to caching
🧠 Best Practices

✅ Set appropriate TTL values — balance freshness and performance.
✅ Use consistent hashing for distributed caches.
✅ Monitor hit/miss ratios continuously.
✅ Avoid caching sensitive or user-specific data unless encrypted.
✅ Implement cache warming during startup to reduce cold misses.
✅ Combine CDN + server-side cache for layered caching.

💥 Common Pitfalls

Stale data served due to improper invalidation

Cache stampede (multiple requests miss cache simultaneously)

Over-caching dynamic or personalized content

Memory bloat due to no eviction

Inconsistent cache population across distributed nodes

⚠️ Mitigation Tip: Use “lock-and-populate” or “request coalescing” patterns to prevent cache stampedes.

🌐 Real-World Examples
System	Caching Layer	Description
YouTube	CDN + Redis	Caches video metadata and recommendations
Twitter	Redis + Memcached	Caches timelines and user sessions
Netflix	Edge caching via CDN	Delivers global video content efficiently
Facebook	TAO + Memcache	Custom caching system for social graph queries
GitHub	Redis-based page cache	Reduces DB reads on heavy API endpoints
✅ Caching Checklist

☑️ Identify high-read or repetitive workloads
☑️ Choose appropriate cache type (in-memory, distributed, CDN)
☑️ Implement invalidation and TTL policies
☑️ Monitor hit/miss ratios and latency
☑️ Plan for failover or cache miss fallback
☑️ Secure cache data (especially in shared environments)

📚 Further Reading

Designing Data-Intensive Applications – Martin Kleppmann

Redis Documentation – Caching Best Practices

Google Cloud CDN Architecture

Netflix Edge Architecture

Facebook TAO: The Power of the Graph Cache
