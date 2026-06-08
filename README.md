#  Networking Task 02: Network Devices & IP Addressing

> **Internship Assignment** | Network Devices & IP Addressing | Varsha Kerketta

---

## Overview

This task covers the identification and function of core network devices, IP address classification (public vs. private), understanding your local network configuration, tracing the communication flow from device to server, and hands-on command-line networking exercises.

---

##  Repository Structure

```
Networking_Task_02/
├── README.md
└── Networking_Task_02_Varsha_Kerketta.pdf
```

---

##  Task Breakdown

### Part A — Network Devices Research

A study of six essential networking devices, how they work, and their real-world usage:

| Device | Function | Real-World Example |
|--------|----------|--------------------|
| **Router** | Connects different networks; directs data using IP routing tables | Home Wi-Fi router connecting devices to the internet |
| **Switch** | Connects devices within a LAN; uses MAC addresses to send data only to the intended device | Computer lab connecting PCs to a server |
| **Hub** | Broadcasts incoming data to all connected devices (largely replaced by switches) | Legacy small office networks |
| **Access Point (AP)** | Extends a wired network wirelessly via Wi-Fi signals | Campus-wide Wi-Fi using multiple APs |
| **Firewall** | Monitors and filters network traffic based on security rules | Blocking unauthorized access to a corporate network |
| **Modem** | Converts digital signals for transmission over ISP lines (telephone, cable, fiber) | Broadband connection receiving signal from ISP |

---

### Part B — IP Address Classification

| IP Address | Type | Reason |
|------------|------|--------|
| `192.168.1.10` |  Private | Falls in the `192.168.0.0/16` range — used in home/office LANs |
| `10.0.0.5` |  Private | Falls in the `10.0.0.0/8` range — used in large private networks |
| `172.16.5.20` |  Private | Falls in the `172.16.0.0/12` range — reserved for internal use |
| `8.8.8.8` |  Public | Google Public DNS — globally accessible over the internet |
| `1.1.1.1` |  Public | Cloudflare DNS — reachable from anywhere on the internet |
| `192.168.100.1` |  Private | Falls in the `192.168.0.0/16` range — commonly used as a router's local address |

---

### Part C — Understanding Your Network

System network details captured using `ipconfig /all` on Windows:

| Detail | Value |
|--------|-------|
| Hostname | `LAPTOP-HOME` |
| IPv4 Address | `192.168.1.15` |
| Subnet Mask | `255.255.255.0` |
| Default Gateway | `192.168.1.1` |
| DNS Servers | `8.8.8.8`, `8.8.4.4` |
| DHCP Enabled | Yes |

**Key Observations:**

1. **IP Range** — The device IP `192.168.1.15` belongs to the `192.168.1.0/24` range (`192.168.1.0 – 192.168.1.255`).
2. **Public or Private?** — Private. The `192.168.x.x` range is reserved for local networks and is not directly reachable from the internet.
3. **Router's Role** — The router at `192.168.1.1` acts as the default gateway: it routes traffic between local devices and the internet, assigns IP addresses via DHCP, and provides a layer of network security.
4. **If DNS Stopped Working** — Domain names like `google.com` could not be resolved. Websites would be unreachable by name, though direct IP access might still work. Email and most online services would also break.

---

### Part D — Network Communication Flow

Step-by-step flow of a browser request to `www.google.com`:

```
[ Your Device (192.168.1.15) ]
           |
           |  1. Types www.google.com in browser
           ↓
      [ Router (192.168.1.1) ]
           |
           |  2. Forwards the request to the internet
           ↓
      [ DNS Server (8.8.8.8) ]
           |
           |  3. Resolves www.google.com → 142.250.183.14
           ↓
    [ Google Server (142.250.183.14) ]
           |
           |  4. Sends back the requested web page
           ↓
[ Response Back to Your Device ]
```

| Step | Component | Action |
|------|-----------|--------|
| 1 | Your Device | Sends a request for `www.google.com` |
| 2 | Router | Forwards the request to the internet via the ISP |
| 3 | DNS Server | Translates `www.google.com` → `142.250.183.14` |
| 4 | Google Server | Responds with the requested content |
| 5 | Your Device | Receives and renders the web page |

---

### Part E — Practical Command Exercise

**Commands executed and their outputs:**

#### 1. `ipconfig /all` — View Network Configuration
```
IPv4 Address  . . . . : 192.168.1.100
Default Gateway . . . : 192.168.1.1
DNS Server  . . . . . : 8.8.8.8
```
- **IPv4 Address** — Identifies the device on the local network
- **Default Gateway** — Router that connects the LAN to the internet
- **DNS Server** — Resolves domain names to IP addresses

#### 2. `nslookup google.com` — DNS Lookup
```
Server:  dns.google
Address: 8.8.8.8

Name:    google.com
Address: 142.250.183.14
```
- The DNS server at `8.8.8.8` received the query and returned Google's IP address, enabling the browser to connect to Google's server.

#### 3. `ping google.com` — Test Connectivity & Latency
```
Pinging google.com [142.250.183.14]
Reply from 142.250.183.14: bytes=32 time=25ms TTL=116
```
- Packets were successfully sent and received from Google's server
- Response time: **25ms** — confirms active internet connectivity

---

## 🛠️ Commands Reference

```bash
# View full network configuration
ipconfig /all                  # Windows
ip addr / ifconfig             # Linux

# DNS lookup — resolve domain to IP
nslookup google.com

# Test connectivity and measure latency
ping google.com

# Trace packet path to destination
tracert google.com             # Windows
traceroute google.com          # Linux
```

---

##  Author

**Varsha Kerketta**  
Internship — Networking Module  
Task 02: Network Devices & IP Addressing

---
