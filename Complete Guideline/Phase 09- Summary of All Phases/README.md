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