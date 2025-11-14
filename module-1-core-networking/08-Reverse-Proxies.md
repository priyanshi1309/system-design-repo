# Reverse Proxies

A **reverse proxy** is a server that sits in front of backend servers and handles incoming traffic on their behalf.  
Instead of clients talking directly to application servers, they talk to the reverse proxy, and the reverse proxy decides where each request should go.

If a forward proxy protects clients, a reverse proxy protects servers.

---

## 1. What a Reverse Proxy Does

A reverse proxy sits at the boundary of your infrastructure and manages all external requests.  
It becomes the **single entry point** for clients.

Core responsibilities:
- Receive incoming traffic  
- Route the request to the correct backend server  
- Apply security checks  
- Cache static or repeated content  
- Send the response back to the client  

The client never knows how many servers are behind the reverse proxy.

---

## 2. Why Reverse Proxies Are Used

Reverse proxies offer critical capabilities for modern distributed systems:

### **1. Load Distribution**
Requests can be balanced across multiple servers.  
This improves:
- Throughput  
- Stability  
- Scalability  

### **2. Security Shield**
Backend servers stay hidden from the public internet.  
The reverse proxy can:
- Block attacks (DDoS filtering)  
- Enforce TLS termination  
- Validate headers  

### **3. Caching**
Static assets (images, scripts) can be cached directly at the reverse proxy.  
This reduces unnecessary backend hits.

### **4. SSL/TLS Termination**
Instead of each server handling encryption, the reverse proxy:
- Decrypts incoming traffic  
- Sends plain HTTP to internal services (optional)

This offloads heavy computation.

### **5. Centralized Logging & Monitoring**
You get a single place to monitor traffic.

### **6. Request Routing**
Reverse proxies can send traffic to:
- Different apps  
- Different versions  
- Different microservices  

Used heavily in A/B testing and blue/green deployments.

---

## 3. Common Reverse Proxy Tools

These tools power millions of production systems:

- **Nginx**  
- **HAProxy**  
- **Envoy**  
- **Traefik**  
- **Apache HTTP Server (mod_proxy)**  

They act as both reverse proxies and load balancers.

---

## 4. How a Reverse Proxy Works (Simple Flow)

Client → Reverse Proxy → App Server → Reverse Proxy → Client


1. Client sends a request to your domain (`myapp.com`).  
2. Reverse proxy receives the request.  
3. It chooses which backend server should handle it.  
4. Backend server processes the request.  
5. Response is sent back to the reverse proxy.  
6. Reverse proxy returns the response to the client.

Clients never know:
- Internal IPs  
- How many servers exist  
- Which server served their request  

---

## 5. Practical Examples

### **Example 1: Hosting a Web App**
A reverse proxy routes:
- `/api` to backend API servers  
- `/static` to a caching layer  
- `/auth` to authentication servers  

### **Example 2: Scaling an App**
If your application suddenly grows to millions of users:
- Add more backend servers  
- Reverse proxy spreads load across them  
- No client-side changes needed  

### **Example 3: A/B Testing**
A reverse proxy can send:
- 90% traffic to version A  
- 10% traffic to version B  

---

## 6. Reverse Proxy vs Forward Proxy (Quick Difference)

| Aspect | Forward Proxy | Reverse Proxy |
|-------|---------------|---------------|
| Protects | Client | Server |
| Client sees | Proxy | Proxy |
| Server sees | Proxy instead of client | Reverse proxy instead of backend |
| Common use | Privacy, filtering | Load balancing, security, routing |

Forward proxy = speaks for the **client**.  
Reverse proxy = speaks for the **server**.

---

## 7. Quick Summary

- A reverse proxy sits in front of backend servers.  
- It manages traffic, security, load balancing, caching, and routing.  
- It hides internal infrastructure from the public.  
- It is a critical building block for scalable, resilient system architectures.

This is the gateway for understanding **load balancers**, which you’ll cover next.
