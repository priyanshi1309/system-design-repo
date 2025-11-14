# TCP vs UDP

TCP and UDP are two core transport protocols that define how data travels between devices. Both operate at **Layer 4**, but they serve different purposes and behave differently in terms of reliability, speed, and usage patterns.

---

## 1. Transmission Control Protocol (TCP)

TCP provides **reliable, ordered, and error-checked** delivery of data. It ensures that whatever is sent from one device reaches the other exactly as intended.

### Key Characteristics
- **Connection-oriented**  
  A TCP connection must be established before data transfer using a three-way handshake.
  
- **Guaranteed delivery**  
  Lost packets are retransmitted automatically.

- **Ordered data transfer**  
  Packets arrive in sequence.

- **Flow control & congestion control**  
  Prevents overwhelming the network or the receiver.

- **Heavy but safe**  
  More overhead due to acknowledgments and retransmissions.

### When TCP Makes Sense
- Web pages (HTTP/HTTPS)  
- File transfer (FTP, SFTP)  
- Database connections  
- Emails  
- Any system where *correctness matters more than speed*

### Simple Example  
When loading a banking site, every packet must arrive correctly and in order. Losing or corrupting data isn’t acceptable, so TCP is used for guaranteed precision.

---

## 2. User Datagram Protocol (UDP)

UDP is **fast, lightweight, and connectionless**. It sends data without verifying whether the receiver got it.

### Key Characteristics
- **No handshake**  
  Sends data immediately.

- **No guaranteed delivery**  
  If packets are lost, they are simply gone.

- **No ordering**  
  Packets may arrive out of sequence.

- **Very low latency**  
  Ideal for real-time applications.

- **Minimal overhead**  
  Faster but riskier than TCP.

### When UDP Makes Sense
- Video streaming  
- Online gaming  
- Voice calls (VoIP)  
- Live sports broadcasts  
- DNS queries  
- Any scenario where *speed matters more than perfection*

### Simple Example  
In a video call, it’s better to skip a dropped frame than wait for a retransmission. Real-time experience wins over accuracy.

---

## 3. Side-by-Side Comparison

| Feature | TCP | UDP |
|--------|-----|-----|
| Connection | Connection-oriented | Connectionless |
| Delivery Guarantee | Yes | No |
| Order Guarantee | Yes | No |
| Speed | Slower | Faster |
| Overhead | Higher | Very low |
| Use Cases | Web, banking, APIs, files | Streaming, gaming, VoIP, DNS |
| Packet Loss Handling | Retransmits | Ignores |

---

## 4. Real-World System Design Relevance

- **Load balancers** may operate in TCP mode or UDP mode.  
- **Reverse proxies** typically rely on TCP (since HTTP is built on TCP).  
- **Streaming systems**, IoT, and gaming backends often leverage UDP.  
- **Microservices** normally rely on TCP for stability.  
- **DNS** uses UDP by default for speed, TCP only when responses are large.

---

## 5. Quick Summary  
- **TCP**: Reliable, slow, strict.  
- **UDP**: Fast, loose, efficient.  

Use TCP when correctness is critical.  
Use UDP when speed and real-time response matter more than perfect accuracy.
