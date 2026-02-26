## 1️⃣ What is Azure Redis?

- Azure Cache for Redis is Microsoft’s managed Redis service on Microsoft Microsoft Azure.
- It is a fully managed, in-memory data store based on Redis.

<img width="964" height="295" alt="image" src="https://github.com/user-attachments/assets/b41e8654-ec7c-463b-9b03-92fa64d452dd" />

__Strong Interview Summary Statement:__
```
Azure Cache for Redis is a fully managed in-memory caching service on Azure used to improve application performance, 
reduce database load, and enable distributed application patterns like session storage, distributed locking, and real-time messaging. 
It supports high availability, clustering, persistence, and enterprise-grade security features.
```

__Used for:__
```
- Caching
- Session storage
- Real-time analytics
- Pub/Sub messaging
- Distributed locking
```

## 2️⃣ Why Use Azure Redis?
🔹 Performance: 

```
In-memory → microsecond latency
Reduces database load
Improves application throughput
```
🔹 Scalability

```
Scale up (bigger SKU)
Scale out (clustered mode)
```

🔹 Managed Service

```
Patching handled by Azure
Built-in monitoring
SLA-backed
```
<img width="1894" height="957" alt="image" src="https://github.com/user-attachments/assets/2b7edf6a-be95-459f-af22-7c28018f7b91" />
<img width="1894" height="957" alt="image" src="https://github.com/user-attachments/assets/81737145-6588-4b25-9ab2-27b53d15d212" />
<img width="1866" height="813" alt="image" src="https://github.com/user-attachments/assets/b0bfab20-5589-47ea-aed8-923b8e61f6cd" />


### 4️⃣ Core Redis Data Structures

Redis supports:
```
String
Hash
List
Set
Sorted Set (ZSET)
Bitmap
HyperLogLog
Stream
```
Example:
```
SET user:1 "John"
HSET user:1 name "John" age 30
```

### 5️⃣ Common Interview Use Cases

✅ Caching

```
Cache DB queries
Reduce latency
TTL support

App → Redis → DB (fallback)
```

✅ Distributed Session Store - Used in stateless web apps.
✅ Pub/Sub - Real-time notifications

### 7️⃣ High Availability in Azure

```
Standard & Premium:
Primary + Replica
Automatic failover
SLA (99.9%+)
```
Premium:
```
Geo-replication
Zone redundancy
```

### 8️⃣ Persistence

Two types:
RDB
```
Snapshot-based
Faster recovery
```
AOF
```
Logs every write
More durable
```
Premium tier supports persistence.

### 🔟 Scaling

- Vertical Scaling : Change SKU size
- Horizontal Scaling (Cluster Mode)
```
Data sharded across nodes
Hash slots (0–16383)
Better for large datasets
```
### 1️⃣ Monitoring

Using:

- Azure Monitor
- Metrics:
```
CPU
Memory
Connected clients
Cache hits/misses  [ Important Interview Metric ]
Evicted keys
```
<img width="1177" height="982" alt="image" src="https://github.com/user-attachments/assets/88f1449e-afa3-4329-bf35-d79cb8cafeb5" />
