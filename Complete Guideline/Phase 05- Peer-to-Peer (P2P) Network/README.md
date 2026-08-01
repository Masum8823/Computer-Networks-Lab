# 05. Peer-to-Peer (P2P) Network

> [!NOTE]
> Peer-to-Peer (P2P) Network হলো Computer Networks-এর সবচেয়ে সহজ Network Architecture। ছোট Office, Home Network এবং Lab Practice-এ এটি বেশি ব্যবহৃত হয়।

---

# Table of Contents

- What is Peer-to-Peer Network?
- Characteristics
- Architecture
- How It Works
- Packet Tracer Configuration
- IP Configuration
- Testing Connectivity
- Advantages
- Disadvantages
- P2P vs Client-Server
- Viva Questions
- Common Mistakes
- Quick Revision

---

# What is a Peer-to-Peer (P2P) Network?

**Peer-to-Peer (P2P)** হলো এমন একটি Network যেখানে **সব Computer সমান (Equal)**।

এখানে কোনো Dedicated Server থাকে না।

প্রতিটি Computer প্রয়োজনে **Client** এবং **Server**—দুইভাবেই কাজ করতে পারে।

> [!IMPORTANT]
> **No Dedicated Server = Peer-to-Peer Network**

---

# P2P Architecture

```mermaid
graph LR

PC1 <--> PC2
```

উভয় Computer সরাসরি একে অপরের সাথে Data Share করতে পারে।

---
# Characteristics

- No Dedicated Server
- All Computers are Equal
- Easy to Setup
- Low Cost
- Suitable for Small Networks
- Direct Resource Sharing

---

# How Peer-to-Peer Works

ধরো দুটি Computer আছে।

```text
PC1 ------------ PC2
```

PC1 একটি File Share করলো।

↓

PC2 সরাসরি File Access করলো।

↓

কোনো Server ব্যবহার হলো না।

---

# Packet Tracer Lab

## Step 1

Packet Tracer খুলুন।

---

## Step 2

দুটি PC নিন।

```text
PC0

PC1
```

---

## Step 3

Copper Cross-Over Cable দিয়ে Connect করুন।

```text
PC0 ----------- PC1
```

> [!TIP]
> Packet Tracer-এর Basic Lab-এ সাধারণত **Copper Cross-Over Cable** ব্যবহার করা হয়।

---

# IP Configuration

## PC0

```text
IP Address : 192.168.1.1

Subnet Mask : 255.255.255.0
```

---

## PC1

```text
IP Address : 192.168.1.2

Subnet Mask : 255.255.255.0
```

> [!IMPORTANT]
> দুইটি PC-কে একই Network-এর IP দিতে হবে।

---
# Network Diagram

```mermaid
graph LR

PC0["192.168.1.1"]

PC1["192.168.1.2"]

PC0 <-- Copper Cross-Over --> PC1
```

---
# Testing Connectivity

PC0-এর Command Prompt খুলে লিখুন—

```bash
ping 192.168.1.2
```

যদি নিচের মতো Reply আসে—

```text
Reply from 192.168.1.2

Bytes=32

Time<1ms

TTL=128
```

তাহলে Connection সফল।

---

# Ping Flow

```mermaid
graph LR

PC0 -->|"ICMP Echo Request"| PC1

PC1 -->|"ICMP Echo Reply"| PC0
```

---
# Advantages

- Easy Setup
- Low Cost
- No Dedicated Server Required
- Easy File Sharing
- Suitable for Home Network
- Suitable for Small Office

---
# Disadvantages

- Low Security
- No Central Management
- Difficult Backup
- Performance কমে যায় যখন Computer সংখ্যা বাড়ে

---
# Peer-to-Peer vs Client-Server

| Peer-to-Peer | Client-Server |
|---------------|--------------|
| No Dedicated Server | Dedicated Server থাকে |
| Low Cost | High Cost |
| Easy Setup | Complex Setup |
| Small Network | Large Network |
| Low Security | High Security |

---
# Common Errors

> [!WARNING]
> Different Network-এর IP দিলে Ping হবে না।

---

> [!WARNING]
> একই IP দুইটি PC-তে দিলে **IP Conflict** হবে।

---

> [!WARNING]
> ভুল Cable ব্যবহার করলে Link Down হতে পারে।

---
# Viva Questions

### 1. Peer-to-Peer Network কী?

যে Network-এ Dedicated Server থাকে না এবং সব Computer সমানভাবে কাজ করে।

---

### 2. Dedicated Server থাকে?

না।

---

### 3. প্রতিটি Computer কী হিসেবে কাজ করতে পারে?

Client এবং Server—দুইভাবেই।

---

### 4. Peer-to-Peer কোথায় ব্যবহার করা হয়?

- Home Network
- Small Office
- Computer Lab

---

### 5. Peer-to-Peer-এর সবচেয়ে বড় সুবিধা কী?

Easy Setup এবং Low Cost।

---

### 6. সবচেয়ে বড় অসুবিধা কী?

Security কম।

---

### 7. Ping কেন ব্যবহার করা হয়?

Connection পরীক্ষা করার জন্য।

---

### 8. Ping কোন Protocol ব্যবহার করে?

ICMP

---

### 9. দুইটি PC-এর IP একই হলে কী হবে?

IP Conflict হবে।

---

### 10. দুইটি PC Different Network-এ থাকলে Ping হবে?

না।

---
# Quick Revision

- P2P = Peer-to-Peer
- No Dedicated Server
- All Computers are Equal
- Client + Server একই Computer হতে পারে
- Small Network
- Low Cost
- Easy Setup
- ICMP = Ping
- Same Network IP Required
- Wrong IP = Ping Fail

---
# Exam Tips

> [!TIP]
> Viva-তে "Peer-to-Peer আর Client-Server-এর পার্থক্য" প্রায়ই জিজ্ঞেস করা হয়।

> [!IMPORTANT]
> মনে রাখবে—
>
> - No Dedicated Server
> - Equal Computers
> - Same Network IP
> - Ping = ICMP
> - Cross-Over Cable (Lab Context)