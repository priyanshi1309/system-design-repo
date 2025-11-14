# Load Balancers

Load balancers are systems that distribute incoming traffic across multiple servers so no single machine gets overwhelmed. Think of them as traffic managers making sure requests are routed efficiently, reliably, and without bottlenecks.

---

## Why Load Balancing Matters

When an application scales, one server can’t handle all incoming requests. A load balancer:
- Improves availability by redirecting traffic if a server fails.
- Improves scalability by spreading load across multiple servers.
- Improves performance by routing requests intelligently.

---

## Core Responsibilities

### 1. Traffic Distribution  
A load balancer forwards requests to backend servers using strategies like:
- **Round Robin**: Each server gets a turn.
- **Least Connections**: Server with the fewest active connections gets the next request.
- **IP Hash**: Client IP decides the server (useful for sticky sessions).
- **Weighted Distribution**: More powerful servers get more traffic.

### 2. Health Checks  
The load balancer continuously checks whether backend servers are healthy:
- If a server fails or becomes slow, it’s removed from the pool.
- Once it recovers, it’s added back automatically.

### 3. Failover  
If one server or even an entire availability zone fails, the load balancer reroutes traffic to operational servers.

### 4. SSL/TLS Termination  
The load balancer can decrypt HTTPS traffic before forwarding it to servers.  
This improves backend performance because heavy cryptography moves away from application servers.

### 5. Session Persistence (Sticky Sessions)  
When required, a load balancer can ensure requests from a specific user always go to the same server.

---

## Types of Load Balancers

### Layer 4 Load Balancers  
Operate at the **Transport Layer**, using IP and port information.  
Characteristics:
- Extremely fast  
- Limited routing logic  
- Often used for TCP/UDP-based traffic  
- Examples: AWS NLB, HAProxy (L4 mode)

### Layer 7 Load Balancers  
Operate at the **Application Layer**, aware of HTTP/HTTPS protocols.  
Characteristics:
- Can route based on URL paths, headers, cookies, request type  
- Support advanced rules like redirecting `/api` to a different service  
- Examples: AWS ALB, Nginx, Envoy, Traefik

---

## Algorithms (More Details)

### Round Robin  
Simple and effective for similar-capacity servers.

### Least Response Time  
Routes to the server responding fastest, ensuring optimal client experience.

### Weighted Round Robin  
Servers with higher capacity (more CPU/RAM) get a larger share of traffic.

### Consistent Hashing  
Useful for caching systems to avoid cache misses.

---

## Where Load Balancers Fit in Architecture

Typical setup:

Client → Load Balancer → Multiple Backend Servers → Database


Modern distributed systems often use multiple layers of load balancers:
- **External LB**: Handles public traffic.
- **Internal LB**: Balances microservices inside the network.
- **Service Mesh LB**: Each service has its own sidecar load balancing logic.

---

## Example: Real-World Workflow

1. A user opens your website.  
2. DNS resolves your domain to your load balancer’s IP.  
3. The load balancer receives the request.  
4. It checks which backend server is healthy and least loaded.  
5. It forwards the request accordingly.  
6. If the server crashes mid-day, traffic automatically shifts to other servers.  

The user never notices.

---

## High Availability With Load Balancers

Load balancers themselves can be single points of failure, so systems often use:
- Active-active configuration (two LBs sharing load)
- Active-passive failover (secondary LB activates only after failure)
- Multi-region replication and routing

---

## When to Use Load Balancers

Use them when:
- App traffic is increasing  
- Uptime is crucial  
- Multiple servers or microservices exist  
- Zero downtime deployments are needed  

Avoid when:
- You’re running a very small local setup or a single-server prototype

---

## Summary

Load balancers:
- Spread traffic  
- Prevent failures  
- Boost performance  
- Enable scaling  
- Work at L4 or L7  
- Are essential for modern applications  

They’re the backbone of any production-grade backend system.
