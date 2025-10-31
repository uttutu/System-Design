🌍 Availability in System Design

Availability measures how often a system is operational and accessible when needed.
It reflects the uptime and resilience of your system under normal and adverse conditions.

In short — availability ensures your system is “there when you need it.”

⚖️ Key Concepts
Concept	Description
Uptime	The percentage of time a system is functional and reachable.
Downtime	Periods when the system is unavailable or degraded.
High Availability (HA)	Designing systems to operate continuously without interruption.
Redundancy	Having duplicate components or services that can take over automatically.
Failover	Switching to a backup system when the primary one fails.
Fault Tolerance	The system’s ability to continue functioning despite partial failures.
📈 Availability Targets ("The Nines")
Availability	Downtime per Year	Example
99%	~3.65 days	Standard SLA
99.9% ("three nines")	~8.76 hours	Good for internal systems
99.99% ("four nines")	~52 minutes	Enterprise-grade
99.999% ("five nines")	~5.26 minutes	Mission-critical systems
99.9999% ("six nines")	~31.5 seconds	Ultra-high availability

🎯 The higher the availability target, the greater the cost, complexity, and redundancy required.

⚙️ Strategies to Achieve High Availability
Strategy	Description	Examples
Redundancy & Replication	Duplicate critical components or services	Multi-AZ databases, load-balanced servers
Load Balancing	Distribute requests to healthy nodes	Nginx, AWS ELB, GCP Load Balancer
Failover Mechanisms	Automatically switch to standby systems	DNS failover, database failover clusters
Health Checks & Monitoring	Detect failures early and replace unhealthy nodes	Kubernetes probes, Prometheus alerts
Stateless Services	Simplify scaling and replacement of instances	Session storage in Redis, S3
Geo-Replication	Deploy across multiple regions for fault isolation	AWS Multi-Region, CloudFront, GCP Global Load Balancing
🧩 Availability Patterns
1. Active-Active Architecture

All nodes handle traffic simultaneously.

✅ No downtime during failover.

❌ Requires strong consistency and replication management.

2. Active-Passive Architecture

One node is active while the other remains on standby.

✅ Easier to implement.

❌ Small downtime during failover.

3. Quorum-Based Systems

Operations succeed only when a majority of nodes agree, ensuring continuity during partial failures.

Example: etcd, Cassandra, Consul.

4. Graceful Degradation

When part of the system fails, provide limited but functional service instead of full outage.

Example: Read-only mode when writes fail.

5. Circuit Breaker + Retry Pattern

Prevent cascading failures and maintain partial availability under high error rates.

🧮 Availability Metrics
Metric	Description	Goal
Availability (%)	(Uptime ÷ Total Time) × 100	≥ Target SLO
MTBF	Mean Time Between Failures	High
MTTR	Mean Time To Repair/Recover	Low
Error Rate	% of failed requests	As low as possible
SLA Compliance	% of time meeting promised availability	> 99%
🧠 Design Practices for Availability

✅ Deploy across multiple zones and regions.
✅ Avoid single points of failure (SPOF).
✅ Automate failover and recovery.
✅ Keep services stateless and self-healing.
✅ Use health checks, auto-restart, and graceful rollouts.
✅ Ensure real-time monitoring and alerting.
✅ Regularly test failure scenarios (chaos testing, DR drills).

💥 Common Pitfalls

Relying on a single data center or AZ.

Neglecting DNS or load balancer redundancy.

Manual failover procedures.

Long recovery times (high MTTR).

Overlooking dependencies’ availability (APIs, databases, etc.).

🌐 Real-World Examples
System	Availability Approach
Netflix	Multi-region deployments, chaos testing, auto-healing
AWS S3	11 nines durability, multi-region redundancy
Google Cloud	Load-balanced, multi-zonal architecture
Kubernetes	Self-healing controllers, liveness/readiness checks
✅ Availability Checklist

☑️ Multi-AZ or multi-region setup
☑️ Load balancing with health checks
☑️ Automated failover and backups
☑️ Redundant network and DNS configuration
☑️ Low MTTR and tested recovery plan
☑️ Monitoring, alerting, and chaos drills

📚 Further Reading

Google SRE Book – Availability Chapter

AWS Well-Architected Framework – Reliability Pillar

Netflix Chaos Engineering Blog

Designing for Availability – Microsoft Architecture Center
