# 09. Final Lab Exam Revision

> [!IMPORTANT]
> এই Chapter-টি শুধুমাত্র **Quiz, Viva এবং Lab Final Exam**-এর দ্রুত Revision-এর জন্য তৈরি করা হয়েছে।

---

# One Night Revision Sheet

## Network Basics

| Question | Answer |
|----------|--------|
| Computer Network | Data ও Resource Sharing System |
| Node | Network-এর সাথে Connected Device |
| Host | IP Address থাকা Device |
| Client | Service Request করে |
| Server | Service প্রদান করে |
| Protocol | Communication Rules |

---

# Network Types

| Type | Coverage |
|------|----------|
| PAN | Personal |
| LAN | Room / Building |
| MAN | City |
| WAN | Country / World |

---

# Network Devices

| Device | Layer | Uses |
|---------|-------|------|
| Hub | Layer 1 | Broadcast |
| Switch | Layer 2 | MAC Address |
| Router | Layer 3 | IP Address |
| Bridge | Layer 2 | Connect LAN Segments |
| Repeater | Layer 1 | Signal Boost |
| Modem | Layer 1 | Digital ↔ Analog |
| Access Point | Layer 2 | Wireless Network |

---

# IP Address

## IPv4

- 32 Bit
- 4 Octets

Example

```text
192.168.1.10
```

---

## IPv6

- 128 Bit

Example

```text
2001:db8::1
```

---
# IP Classes

| Class | Range | Default Mask |
|------|---------|--------------|
| A | 1–126 | 255.0.0.0 |
| B | 128–191 | 255.255.0.0 |
| C | 192–223 | 255.255.255.0 |
| D | 224–239 | Multicast |
| E | 240–255 | Research |

---

# Private IP Range

| Class | Range |
|------|---------|
| A | 10.0.0.0 – 10.255.255.255 |
| B | 172.16.0.0 – 172.31.255.255 |
| C | 192.168.0.0 – 192.168.255.255 |

---

# Special IP Address

| Address | Purpose |
|----------|----------|
| 127.0.0.1 | Loopback |
| 169.254.x.x | APIPA |

---

# Address Summary

| Name | Meaning |
|------|----------|
| IP Address | Logical Address |
| MAC Address | Physical Address |
| Network Address | First Address |
| Broadcast Address | Last Address |
| Default Gateway | Router-এর IP |

---

# Cable Summary

| Cable | Uses |
|---------|------|
| Straight Through | Different Devices |
| Cross Over | Same Devices |
| Console | Configure Router/Switch |
| Fiber | Long Distance |

---
# ARP

**ARP = Address Resolution Protocol**

কাজ:

IP Address → MAC Address

ARP Request = Broadcast

ARP Reply = Unicast

Command

```bash
arp -a
```

---

# ICMP

**ICMP = Internet Control Message Protocol**

Uses

- Ping
- Error Reporting

Command

```bash
ping 192.168.1.1
```

---

# Ping Flow

```text
ARP Request

↓

ARP Reply

↓

ICMP Echo Request

↓

ICMP Echo Reply

↓

Success
```

---

# Router Commands

```bash
enable

configure terminal

interface g0/0

ip address 192.168.1.1 255.255.255.0

no shutdown

end
```

---
# RIP Commands

```bash
router rip

version 2

network 192.168.1.0

network 10.0.0.0

no auto-summary
```

---
# Verification Commands

```bash
show ip route
```

```bash
show running-config
```

```bash
show ip protocols
```

---

# Hub vs Switch vs Router

| Feature | Hub | Switch | Router |
|----------|-----|--------|---------|
| Layer | 1 | 2 | 3 |
| Address | None | MAC | IP |
| Broadcast | Yes | No | No |
| Speed | Low | High | High |
| Connects | Same LAN | Same LAN | Different LAN |

---

# Peer-to-Peer

- No Dedicated Server
- Low Cost
- Easy Setup
- Small Network
- All Computers Equal

---

# RIP

- Dynamic Routing Protocol
- Distance Vector
- Metric = Hop Count
- Maximum Hop = 15
- Hop 16 = Unreachable

---

# Most Important Commands

```bash
ping
```

```bash
arp -a
```

```bash
ipconfig
```

```bash
tracert
```

```bash
show ip route
```

```bash
show running-config
```

---

# 30 Most Common Viva Questions

### 1. Computer Network কী?
দুই বা ততোধিক Device-এর মধ্যে Data ও Resource Share করার ব্যবস্থা।

### 2. Node কী?
Network-এর সাথে Connected যেকোনো Device।

### 3. Host কী?
IP Address থাকা Device।

### 4. Protocol কী?
Communication Rules।

### 5. Hub কোন Layer?
Layer 1

### 6. Switch কোন Layer?
Layer 2

### 7. Router কোন Layer?
Layer 3

### 8. Switch কোন Address ব্যবহার করে?
MAC Address

### 9. Router কোন Address ব্যবহার করে?
IP Address

### 10. IPv4 কত Bit?
32 Bit

### 11. IPv6 কত Bit?
128 Bit

### 12. Loopback Address কত?
127.0.0.1

### 13. APIPA Range কত?
169.254.0.0/16

### 14. Default Gateway কী?
Router-এর IP Address।

### 15. Private IP Range বলো।
10.x.x.x, 172.16–31.x.x, 192.168.x.x

### 16. ARP-এর কাজ কী?
IP → MAC Address বের করা।

### 17. ARP Request কেমন?
Broadcast

### 18. ARP Reply কেমন?
Unicast

### 19. Ping কোন Protocol ব্যবহার করে?
ICMP

### 20. ICMP-এর কাজ কী?
Network Test ও Error Reporting।

### 21. RIP-এর পূর্ণরূপ কী?
Routing Information Protocol।

### 22. RIP কোন Metric ব্যবহার করে?
Hop Count

### 23. Maximum Hop Count কত?
15

### 24. Hop 16 মানে কী?
Destination Unreachable

### 25. Peer-to-Peer কী?
Dedicated Server ছাড়া Network।

### 26. Straight Cable কোথায় ব্যবহার হয়?
Different Devices

### 27. Cross Cable কোথায় ব্যবহার হয়?
Same Devices

### 28. Console Cable-এর কাজ কী?
Router/Switch Configure করা।

### 29. `no shutdown` কেন ব্যবহার করা হয়?
Interface চালু করার জন্য।

### 30. `show ip route` কী দেখায়?
Routing Table।

---

# Final Exam Tips

> [!TIP]
> নিচের জিনিসগুলো অবশ্যই মুখস্থ রাখবে:
>
> - Hub → Layer 1
> - Switch → Layer 2
> - Router → Layer 3
> - Switch → MAC
> - Router → IP
> - IPv4 → 32 Bit
> - IPv6 → 128 Bit
> - Loopback → 127.0.0.1
> - APIPA → 169.254.x.x
> - ARP = IP → MAC
> - ICMP = Ping
> - RIP = Hop Count
> - Maximum Hop = 15
> - Hop 16 = Unreachable
> - Default Gateway = Router IP

---