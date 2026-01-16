# Mapping network protocols to OSI model layers

The OSI model is a conceptual framework that standardizes the functions of a network into 7 layers. 
Each layer has its own role, and different network protocols operate at different layers. 
Here’s a clear mapping of common protocols to OSI layers:

OSI model layers and their protocols 

| Layer | Function | Key Protocols and Technologies |
|-------|----------|--------------------------------|
| Layer 7: <br> **Application** | Provides network services directly to the user, such as email, file transfers, and web browsing. | HTTP/HTTPS, FTP, SMTP, DNS |
| Layer 6: <br> **Presentation** | Translates, encrypts, and compresses data to ensure it's in a usable format for the application layer. | TLS/SSL, MIME |
| Layer 5: <br> **Session** | Manages sessions between applications, including setting up, maintaining, and terminating connections. | NetBIOS, RPC, PPTP |
| Layer 4: <br> **Transport** | Provides reliable or "best-effort" data delivery between hosts, managing segments and datagrams. | TCP, UDP |
| Layer 3: <br> **Network** | Handles logical addressing, routing, and forwarding of data packets across different networks. | IP, ICMP, OSPF |
| Layer 2: <br> **Data Link** | Ensures reliable data transfer across a single physical link, handling physical addressing and error detection for frames. | Ethernet, PPP, Wi-Fi (802.11) |
| Layer 1: <br> **Physical** | Transmits raw bits of data over the physical network medium, such as cables or wireless signals. | USB, SONET/SDH, Ethernet (physical standards) |

A simpler way to remember:
- L1-L2 → moving **bits and frames**
- L3-L4 → moving **packets and segments**
- L5-L7 → handling **connections, encryption, and applications**
