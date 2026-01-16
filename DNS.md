# What DNS protocol is and what is it for

**DOMAIN NAME SYSTEM**

It is a protocol and system that translates **human-readable domain names** (like example.com) <br> **into IP addresses** (like 93.184.216.34) that computers use to communicate over the Internet.


What DNS is used for
1. **Resolving Domain Names to IP Addresses**


- When you type a website URL in your browser, DNS resolves the domain name to the IP address of the server hosting that website.
- Example: www.google.com → 142.250.190.100.


2. **Email Routing**


- DNS helps route emails by using **MX (Mail Exchange) records** that point to mail servers for a domain.


3. **Load Balancing and Redundancy**


- DNS can distribute traffic across multiple servers using techniques like **Round Robin DNS**.


4. **Service Discovery**


- Certain DNS records (like **SRV**) help locate specific services within a network.


| Record | Purpose |
|--------|---------|
| **A** <br> | Maps a domain to an IPv4 address |
| **AAAA** <br>| Maps a domain to an IPv6 address |
| **CNAME** <br>| Alias of another domain |
| **MX** <br>| Mail server for a domain |
| **TXT** <br>| Text information, often for verification |
| **NS** <br> nameserver | Authoritative name servers for a domain (specifies which name servers are authoritative for a domain) |
| **SRV** <br> | Location of services (specifies a host and port for specific services) |
