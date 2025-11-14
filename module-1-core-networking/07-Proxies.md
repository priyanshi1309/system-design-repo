# Proxies

A **proxy** is a server that sits between a client and the internet. It forwards client requests to external servers and returns the responses back to the client. Think of it as a middle agent that can filter, hide, protect, or modify traffic before it reaches the destination.

---

## 1. What a Proxy Actually Does

A proxy acts on behalf of the client.  
Instead of the client directly reaching a website or service, the proxy makes the request for the client.

Core responsibilities:
- Forward client requests  
- Receive server responses  
- Return responses back to the client  

The destination server only sees the **proxy’s IP**, not the real client’s IP.

---

## 2. Why Proxies Exist

Proxies are used for several practical reasons:

### **1. Privacy & IP Masking**
Client identity is hidden.  
Useful for:
- Corporate networks  
- Preventing direct exposure  
- Geolocation masking  

### **2. Access Control**
Organizations use proxies to:
- Block harmful websites  
- Monitor traffic  
- Enforce usage policies  

### **3. Caching**
Proxies can store copies of frequently accessed resources.  
This reduces load and speeds up responses.

### **4. Filtering & Security**
Proxies can:
- Block malicious traffic  
- Remove suspicious content  
- Allow only approved protocols  

### **5. Logging & Monitoring**
Traffic can be inspected or recorded for:
- Auditing  
- Debugging  
- Compliance  

---

## 3. Types of Proxies

### **1. Forward Proxy (regular proxy)**
The most common proxy type.  
Placed *in front of the client*.

Clients → Proxy → Internet

Used for:
- Access control  
- Masking client identity  
- Company-level traffic routing  

### **2. Transparent Proxy**
Client doesn’t know it exists.  
Often used by:
- Schools  
- Offices  
- ISPs  

It intercepts traffic automatically without configuration.

### **3. Anonymous Proxy**
Hides the client’s identity completely.  
Destination can’t trace who made the request.

### **4. High-Anonymity (Elite) Proxy**
Takes masking further by rotating IPs and removing all identifying headers.

---

## 4. How a Proxy Works (Simple Flow)

Client → Proxy → Target Server → Proxy → Client


1. Client sends request to proxy.  
2. Proxy forwards it to the target server.  
3. Server responds back to the proxy.  
4. Proxy returns response to client.  

The client never contacts the server directly.

---

## 5. A Real Example

Imagine a company where all employee internet traffic is routed through a proxy.

**Why?**
- To prevent access to harmful sites  
- To limit bandwidth usage  
- To hide internal network structure  
- To log activity for security  

Employees never talk to the outside world directly.  
The proxy does all communication externally.

---

## 6. Where Proxies Are Used in System Design

Proxies show up in multiple architectural areas:
- Corporate firewalls  
- Access gateways  
- Developer testing tools (Burp Suite, Postman via proxy)  
- Traffic filtering layers  
- API debugging  
- Network isolation boundaries  

They are different from reverse proxies (which sit in front of servers).  
Forward proxies protect clients, not servers.

---

## 7. Quick Summary

- A **proxy** is a middle server between client and destination.  
- It hides client identity, filters traffic, caches data, and enforces controls.  
- It operates on behalf of the client.  
- Used for security, privacy, logging, and performance optimization.

This sets the foundation for understanding **reverse proxies**, which handle traffic in the opposite direction.
