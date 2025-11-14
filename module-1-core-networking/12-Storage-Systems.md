# Storage Systems

Storage systems define how data is stored, organized, accessed, replicated, and managed across different machines. In system design, understanding storage is fundamental because your application will rely on it for durability, speed, and reliability.

Storage systems come in many shapes depending on use cases: databases, distributed file systems, object storage, block storage, caching layers, and more. Each type solves a specific problem.

---

## Why Storage Systems Matter

A system isn’t useful if the data disappears, loads slowly, or fails under high demand. Storage determines:
- How fast data can be read or written  
- How safely data is kept  
- How well the system scales  
- How easy it is to recover from failures  

Good storage design keeps systems stable even during heavy traffic or hardware failure.

---

## Core Categories of Storage

### 1. **Block Storage**
Low-level storage that behaves like a raw hard drive.

Examples:
- AWS EBS  
- Local SSDs  
- SAN devices  

Use cases:
- Databases  
- Operating system disks  
- Applications needing fast I/O  

Characteristics:
- High throughput  
- Low latency  
- Data stored in fixed-size blocks  

---

### 2. **File Storage**
Data stored as files in a hierarchical structure.  
Works like a traditional filesystem.

Examples:
- NFS (Network File System)  
- SMB/CIFS  
- Shared drives  

Use cases:
- Shared file storage  
- Media assets  
- Logs  

Characteristics:
- Easy to manage  
- Familiar structure  
- Good for shared access  

---

### 3. **Object Storage**
Stores data as objects with metadata and a unique ID instead of a file path.

Examples:
- AWS S3  
- Google Cloud Storage  
- Azure Blob Storage  
- MinIO  

Use cases:
- Large media files  
- Backups  
- Logs  
- Static website assets  

Characteristics:
- Highly scalable  
- Cheap storage  
- Ideal for unstructured data  
- No hierarchical folders (flat namespace)

---

## Storage System Attributes

### 1. Durability  
How safe the data is, even if machines fail.

Example:  
S3 promises eleven 9s (99.999999999%) durability.

### 2. Availability  
How often the data is reachable.

### 3. Latency  
How long it takes to get data.

### 4. Throughput  
How much data can be read/written per second.

### 5. Consistency  
Whether all clients see the same data at the same time.

---

## Local vs Distributed Storage

### Local Storage  
Stored on one machine.  
Great for speed, terrible for reliability if the machine dies.

### Distributed Storage  
Data spread across multiple servers.

Benefits:
- No single point of failure  
- Scales horizontally  
- Supports huge data sizes  

Examples:
- HDFS  
- Ceph  
- GlusterFS  
- Cassandra (as a distributed storage engine)  

---

## Data Replication

Replication keeps copies of data across multiple nodes.

Types:
- **Synchronous:** all replicas updated together  
- **Asynchronous:** updates happen later  

Purpose:
- Fault tolerance  
- Faster reads  
- High availability  

---

## Data Sharding

Sharding splits data across nodes so systems can scale horizontally.

Example:
Users A–M on Shard 1
Users N–Z on Shard 2


Sharding helps:
- Balance load  
- Handle large datasets  
- Avoid bottlenecks  

---

## Hot vs Cold Storage

### Hot Storage
- Fast access  
- Expensive  
- SSDs, in-memory caches  

Use cases:
- Active user data  
- Realtime analytics  

### Cold Storage
- Cheap  
- Slow  
- Archival systems  

Use cases:
- Historical logs  
- Backups  

---

## Caching and Storage

Caching is part of the storage strategy, not a database replacement.

Cache examples:
- Redis  
- Memcached  

They store frequently accessed data in memory to reduce load on primary storage.

---

## File System Types

### 1. Traditional Filesystems  
EXT4, NTFS, APFS.

### 2. Distributed Filesystems  
HDFS, CephFS.

### 3. Log-Structured Filesystems  
Optimized for sequential writes (used internally by many distributed systems).

---

## Storage in System Architecture

A typical architecture includes:

Clients → App Servers → Cache → Primary Storage → Backups/Replicas


Each layer is designed to reduce load and improve durability.

---

## Real-World Use Cases

### Photos/Videos  
Object storage (S3)

### User accounts  
Databases (Block storage or distributed DB systems)

### Logs  
Object storage or distributed file stores

### Analytics  
Data lake + distributed storage systems

### High performance apps  
Local SSD + distributed cache + replicated DBs

---

## Summary

Storage systems form the backbone of any reliable architecture. They determine:
- Speed  
- Flexibility  
- Durability  
- Scalability  

Understanding how block, file, and object storage work, along with replication, sharding, caching, and distributed design, prepares you to build systems that run at large scale without falling apart.
