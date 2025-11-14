# CDN (Content Delivery Network)

A CDN is a globally distributed network of servers that deliver content to users from the location closest to them. Instead of every request going all the way to your origin server, a CDN caches content in multiple geographic locations so users get faster load times and lower latency.

---

## Why CDNs Exist

If your server is in Mumbai and a user opens your site from New York, the request travels thousands of kilometers. That means:
- High latency  
- Slow loading  
- Increased server load  

A CDN fixes this by serving cached content from the nearest edge location, drastically improving performance.

---

## Key Responsibilities

### 1. Content Caching  
CDNs store static assets like:
- Images  
- CSS  
- JavaScript  
- Videos  
- HTML (static pages)  

When a user requests a file, the CDN serves it from the nearest edge server.

### 2. Latency Reduction  
Since content comes from a local edge node instead of the origin server, response time drops significantly.

### 3. Offloading Origin Traffic  
Your main server handles fewer requests, improving performance and lowering infrastructure cost.

### 4. DDoS Protection  
Many CDNs absorb massive traffic spikes and malicious requests before they hit your origin.

### 5. Security Enhancements  
CDNs offer:
- WAF (Web Application Firewall)  
- Bot filtering  
- TLS/SSL handling  
- Rate limiting  

### 6. Global Availability  
CDNs ensure your content can be delivered reliably across continents without you deploying multiple servers.

---

## How a CDN Works

1. User requests a resource (e.g., an image).  
2. CDN checks the closest edge server.  
3. If cached, the file is served immediately (cache hit).  
4. If not cached, the CDN fetches the file from the origin (cache miss).  
5. The file is stored at the edge server for future requests.  

---

## Cache Invalidation

CDNs allow you to refresh or purge outdated content:

- **Time-based expiration (TTL)**  
- **Manual purge**  
- **Programmatic cache control using headers**  
  - `Cache-Control`  
  - `ETag`  
  - `Last-Modified`

---

## Types of Content CDNs Handle

### Static Content  
Cached assets that rarely change.

### Dynamic Content (Modern CDNs)  
Some CDNs support smart routing for:
- API responses  
- Personalized content  
- Real-time data  

Examples include Cloudflare Workers, AWS CloudFront Lambda@Edge, Fastly Compute@Edge.

---

## CDN vs Load Balancer

| Feature | CDN | Load Balancer |
|--------|------|----------------|
| Purpose | Speed + caching | Traffic distribution |
| Layer | Mostly Layer 7 | Layer 4 or Layer 7 |
| Focus | Global performance | Backend efficiency |
| Caches content | Yes | No |

Often both are used together:

Client → CDN → Load Balancer → App Servers → Database


---

## Popular CDN Providers

- Cloudflare  
- AWS CloudFront  
- Akamai  
- Fastly  
- Google Cloud CDN  
- Azure CDN  

---

## Real-World Example

When a user in Germany loads your website:
1. DNS routes their request to the nearest CDN edge location (e.g., Frankfurt).  
2. CDN checks for cached assets.  
3. Edge server serves content directly.  
4. Only uncached data reaches your origin.  

This leads to:
- Faster load times  
- Lower server traffic  
- Better user experience globally  

---

## Summary

A CDN:
- Speeds up content delivery  
- Reduces latency  
- Protects your app  
- Reduces server load  
- Supports global scalability  

It’s a core component of modern, high-performance web architecture.
