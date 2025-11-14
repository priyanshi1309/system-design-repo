 # Clustering

Clustering is the strategy of running multiple servers (or nodes) together so they behave like a single system. Instead of depending on one machine, your application runs across several, improving reliability, performance, and scalability.

Clustering is used everywhere: databases, application servers, caches, search engines, analytics pipelines, and anything that must stay online even when parts fail.

---

## Why Clustering Exists

A single machine has limits:
- It can crash  
- It can’t handle infinite traffic  
- It has limited CPU, RAM, and disk  
- Maintenance requires downtime  

Clustering solves these by adding more machines and making them work together.

---

## What Clustering Gives You

### 1. High Availability (HA)
If one node fails, the others keep running.  
This prevents downtime and improves fault tolerance.

### 2. Scalability
You can add more nodes as demand grows (horizontal scaling).

### 3. Load Distribution
Traffic or processing is shared across nodes instead of one machine doing all the work.

### 4. Reliability
If a node goes offline, the cluster automatically reroutes tasks.

---

## How Clustering Works (Simple Flow)

1. Multiple nodes join a cluster.  
2. They share data or state depending on the cluster type.  
3. A coordinator or consensus mechanism decides which node does what.  
4. If a node stops responding, the cluster removes it and keeps operating.  

---

## Types of Clustering

### 1. **Active-Active Cluster**
All nodes work at the same time.

- Every node handles traffic.  
- If one dies, others continue seamlessly.  
- Common for web servers, caches, and message brokers.

### 2. **Active-Passive Cluster**
One node is active, the other waits in standby.

- Used for databases or stateful systems.  
- Passive node becomes active during failure.

---

## Clustering in Databases

Different databases use clustering for different purposes:

- **MongoDB**: replica sets (HA) and sharding (scaling)  
- **PostgreSQL**: primary-replica setups  
- **Cassandra**: shared-nothing cluster  
- **Redis Cluster**: distributed keyspace  

Clustering helps databases scale reads/writes and avoid single points of failure.

---

## Consensus in Clusters

Distributed nodes require agreement on:
- Which node is leader  
- Who stores which data  
- Whether a node is healthy  

Popular algorithms:
- **Raft (most common)**  
- **Paxos**  
- **Gossip protocols**  

These keep the cluster stable even with failures.

---

## Load Balancers & Clusters

Most clusters are paired with load balancers:

Client → Load Balancer → Cluster Nodes


LB distributes traffic across the cluster and checks node health.

---

## Real-World Examples

### Web Tier
Nginx/Node.js servers running in parallel behind a load balancer.

### Database Tier
Primary + multiple replica nodes to scale reads.

### Caching Tier
Redis cluster splitting dataset across multiple nodes.

### Analytics/Scheduling
Kafka partitions data and distributes workload across brokers.

---

## Horizontal vs Vertical Scaling

| Type | Meaning | Pros | Cons |
|------|----------|------|------|
| Vertical Scaling | Upgrading one machine | Simple | Hard limit, expensive |
| Horizontal Scaling | Adding more machines | Infinite scaling, HA | Needs clustering |

Clustering is the backbone of horizontal scaling.

---

## Failure Handling in Clusters

Clusters respond to failure by:
- Replacing the failed node  
- Re-routing traffic  
- Rebalancing data  
- Electing a new leader  
- Triggering replicas to take over  

This ensures smooth, uninterrupted performance.

---

## Clustering Is Not Load Balancing

| Clustering | Load Balancing |
|-----------|----------------|
| Group of machines working together | Traffic distributor |
| Ensures availability and distribution of work | Sends requests to nodes |
| Internal system concept | External infrastructure |

They complement each other but are different components.

---

## Summary

Clustering gives you:
- High availability  
- Fault tolerance  
- Horizontal scalability  
- Improved performance  

It’s one of the core patterns in modern distributed systems and essential for building systems that stay up even during failures or high user demand.

