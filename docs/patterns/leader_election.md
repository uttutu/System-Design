Leader Election
Overview

Leader election is a fundamental concept in distributed systems used to coordinate actions among multiple nodes or processes.
In systems where multiple replicas exist, leader election ensures that one and only one node acts as the “leader” — responsible for making authoritative decisions, maintaining consistency, or orchestrating coordination tasks.

It prevents conflicts, duplicate work, or inconsistent state updates, enabling predictable and reliable system behavior.

Why Leader Election Is Needed

Distributed systems often have multiple nodes that:

Need to coordinate access to shared resources.

Must synchronize state changes or perform write operations.

Should recover from failures without human intervention.

Without leader election, multiple nodes might:

Perform conflicting updates (e.g., two masters writing to a database).

Cause split-brain scenarios in clusters.

Fail to agree on who should handle requests or coordinate actions.

Leader election ensures that only one node acts as the decision-maker, while others act as followers or backups.

Core Concepts
Concept	Description
Leader	The node currently in charge of coordination or control.
Followers	Nodes that replicate data or follow instructions from the leader.
Candidate	A node that attempts to become the leader during an election.
Term/Epoch	Logical time period during which a leader is valid.
Consensus	The process by which nodes agree on who the leader is.
Leader Election Algorithms
1. Bully Algorithm

Each node has a unique ID; the node with the highest ID becomes the leader.

If a leader fails, nodes with lower IDs initiate an election.

✅ Pros: Simple and deterministic.

⚠️ Cons: High message overhead during failures.

2. Raft Consensus Algorithm

Nodes elect a leader through majority voting.

Used by systems like etcd, Consul, and CockroachDB.

✅ Pros: Strong consistency, fault-tolerant.

⚠️ Cons: Slightly slower leader failover under network partitions.

3. Paxos

Classic consensus protocol that ensures agreement on a single leader or value.

✅ Pros: Proven correctness in asynchronous systems.

⚠️ Cons: Complex to implement; not easily understandable.

4. Zookeeper’s Leader Election (ZAB Protocol)

Uses ephemeral znodes; the node with the smallest sequential ID becomes leader.

✅ Pros: Highly reliable and widely used (Kafka, Hadoop).

⚠️ Cons: Depends on centralized coordination (Zookeeper).

5. Lease-Based / Time-Based Election

Leader holds a lease (time-limited lock) and must renew it periodically.

If it fails, another node can acquire leadership.

✅ Pros: Simple and works well with distributed locks.

⚠️ Cons: Risk of overlapping leadership if clock skew occurs.

Key Challenges

🧩 Network Partitions: Can result in multiple leaders (split-brain).

⏱️ Clock Skew: Time-based elections may expire incorrectly.

🔁 Failover Time: Detecting leader failure and electing a new one introduces latency.

⚖️ Consistency vs Availability: Balancing safety and responsiveness in leader transitions.

🧠 State Synchronization: Followers must catch up after leadership changes.

Best Practices

Use a well-tested consensus system like etcd, Zookeeper, or Consul instead of implementing from scratch.

Ensure majority-based quorum for elections to prevent split-brain.

Use ephemeral locks or leases to prevent orphaned leaders.

Implement leader health checks and automatic re-election on failure.

Log term/epoch numbers to track leadership history.

Monitor leader changes to detect instability or flapping.

Common Implementations
System	Leader Election Mechanism	Description
Kubernetes	Leases in etcd	Controllers use leader election to ensure only one active replica performs work.
Kafka	Zookeeper (ZAB protocol)	Elects a controller broker responsible for partition management.
Elasticsearch	Zen Discovery	Uses cluster coordination for master election.
Consul / Nomad	Raft consensus	Elects a leader via Raft for cluster coordination.
Hadoop YARN	Zookeeper	Ensures a single active ResourceManager.
Failure Handling

Leader Failure Detection

Achieved through heartbeats or lease expiration.

Followers trigger a new election after timeouts.

Re-election

Remaining nodes nominate themselves or vote for a new leader.

State Recovery

New leader synchronizes logs or state before resuming operations.

Follower Promotion

Pre-designated secondary node can become leader immediately in some systems.

Advantages

Ensures coordinated control and eliminates conflicting operations.

Enables automatic recovery from node failures.

Simplifies task scheduling, log replication, and distributed consensus.

Limitations

May introduce single-leader bottlenecks under high load.

Failover delays can temporarily reduce availability.

Complexities arise in multi-region or geo-distributed deployments.

Further Reading

Raft Paper: In Search of an Understandable Consensus Algorithm

Paxos Made Simple – Leslie Lamport

Zookeeper Documentation – Leader Election Recipes

Kubernetes Controller Leader Election
