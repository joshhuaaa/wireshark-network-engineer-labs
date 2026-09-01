# Wireshark Network Traffic Investigation

## Overview

This project is a small cybersecurity home lab built using **VMware Workstation Pro** and **Wireshark**.

My aim was to learn how network traffic can be captured and analysed, while developing an understanding of common protocols such as **DNS, TCP and HTTP/HTTPS**.

---

## Lab Setup

| Component        | Setup               |
| ---------------- | ------------------- |
| Host             | Windows PC          |
| Virtualisation   | VMware              |
| Virtual Machine  | Linux               |
| Network          | VMware NAT / VMnet8 |
| Network Analysis | Wireshark           |

---

## Investigation

I generated web traffic from my Linux virtual machine and captured it using Wireshark.

During the investigation, I identified:

* DNS queries used to resolve domain names
* DNS responses containing IP addresses
* TCP connections
* The TCP three-way handshake
* HTTP requests and responses
* Source and destination IP addresses
* Source and destination ports

### Example Traffic Flow

```text
Linux VM
   │
   │ DNS Query
   ▼
DNS Server
   │
   │ IP Address
   ▼
Web Server
   │
   │ TCP Connection
   ▼
HTTP / HTTPS Request
   │
   ▼
Server Response
```

---

## Key Finding

One of the connections I investigated showed the following sequence:

```text
SYN
 ↓
SYN/ACK
 ↓
ACK
 ↓
HTTP GET
 ↓
HTTP Response
```

This helped me understand how a TCP connection is established before application level communication takes place.

I also observed the difference between HTTP and HTTPS traffic. This demonstrated why encryption is important for protecting application data during network communication.

---

## Captures

Wireshark captures from the investigation are available in the [`captures`](./captures) directory.

The captures include examples of:

* DNS queries and responses
* TCP connections and handshakes
* HTTP/HTTPS traffic
* Web traffic generated from the Linux VM

Each capture is labelled with a short description of what was being investigated.


---

## Security Relevance

This lab introduced me to the process of analysing network traffic from a defensive perspective.

A security analyst could use similar techniques to investigate:

* Unusual connections
* Unexpected destinations
* Suspicious protocols
* DNS activity
* Network reconnaissance
* Potentially compromised devices

---

## What I Learned

### Networking

* Packet capture
* DNS
* TCP
* HTTP/HTTPS
* IP addresses and ports
* TCP three-way handshakes
* Network traffic analysis

### Cybersecurity

* Using Wireshark to investigate network activity
* Identifying communication between hosts
* Understanding what information network traffic can reveal
* Understanding the security benefits of encryption
* Using packet evidence to support an investigation

---

## Future Improvements

* [ ] Compare HTTP and HTTPS traffic in more detail
* [ ] Investigate TLS traffic
* [ ] Learn more advanced Wireshark filtering techniques
* [ ] Investigate simulated suspicious traffic in my own lab

---

## Disclaimer

All traffic analysed in this project was generated from systems and networks that I control or have permission to analyse.

This project was conducted for educational and defensive cybersecurity purposes.
