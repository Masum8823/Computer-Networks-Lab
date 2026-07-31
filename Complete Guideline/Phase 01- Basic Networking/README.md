# 01. Basic Networking

> [!NOTE]
> এই Chapter-টি Computer Networks Lab-এর Foundation। পরবর্তী সব Topic বুঝতে হলে প্রথমে এই Chapter ভালোভাবে বুঝতে হবে।

---

# Table of Contents

- What is a Computer Network?
- Why Do We Need a Network?
- Components of a Network
- Node
- Host
- Client
- Server
- Data
- Protocol
- Bandwidth
- Latency
- Types of Network
- Network Topology (Introduction)
- Advantages & Disadvantages
- Viva Questions
- Quick Revision

---

# What is a Computer Network?

A **Computer Network** is a collection of two or more interconnected devices that communicate with each other to share data and resources.

**বাংলায়:**

Computer Network হলো দুই বা ততোধিক Computer বা Device-এর মধ্যে Data এবং Resource Share করার জন্য তৈরি সংযোগ।

### Example

- Home Wi-Fi
- Computer Lab
- Office Network
- University Campus Network

---
# Why Do We Need a Network?

Network ব্যবহারের প্রধান কারণগুলো—

- File Sharing
- Internet Sharing
- Printer Sharing
- Communication
- Resource Sharing
- Centralized Management

---

# Components of a Network

একটি সাধারণ Network-এ সাধারণত নিচের Component থাকে।

- Computer
- Laptop
- Server
- Switch
- Router
- Hub
- Access Point
- Network Cable
- NIC (Network Interface Card)

---
# Node

## Definition

Network-এর সাথে Connected যেকোনো Device-কে **Node** বলা হয়।

### Example

- PC
- Laptop
- Printer
- Router
- Switch

> [!TIP]
> **সব Host হলো Node, কিন্তু সব Node Host নয়।**

---
# Host

## Definition

যে Device-এর নিজস্ব IP Address থাকে এবং Network-এ Data Send/Receive করতে পারে, তাকে **Host** বলে।

### Example

- Computer
- Laptop
- Mobile
- Server

---

# Client

## Definition

যে Device বা Software অন্য Device থেকে Service Request করে, তাকে **Client** বলে।

### Example

তুমি Browser দিয়ে Google খুললে,

তোমার Computer = Client

---
# Server

## Definition

যে Device বা Software Client-এর Request গ্রহণ করে Service প্রদান করে, তাকে **Server** বলে।

### Example

- Google Server
- Facebook Server
- University Server

---
# Client-Server Model

```text
Client -------- Request -------->

Server <-------- Response --------
```

উদাহরণ:

- Browser → Client
- Google → Server

---

# Data

Data হলো এমন Information যা Network-এর মাধ্যমে এক Device থেকে অন্য Device-এ পাঠানো হয়।

### Example

- Text
- Image
- Audio
- Video
- PDF

---

# Protocol

Protocol হলো Communication-এর Rules বা নিয়ম।

যদি দুই Device একই Protocol Follow না করে, তাহলে তারা Communication করতে পারবে না।

### Common Network Protocols

| Protocol | কাজ |
|----------|-----|
| HTTP | Website |
| HTTPS | Secure Website |
| FTP | File Transfer |
| SMTP | Send Email |
| POP3 | Receive Email |
| IMAP | Receive Email |
| DNS | Domain → IP |
| DHCP | Automatic IP Assignment |
| ICMP | Ping |
| ARP | IP → MAC |

> [!IMPORTANT]
> পরীক্ষায় Protocol-এর Definition-এর সাথে অন্তত ২–৩টি Example লিখলে উত্তর আরও ভালো হবে।

---

# Bandwidth

Bandwidth হলো একটি Network প্রতি সেকেন্ডে সর্বোচ্চ কত Data Transfer করতে পারে।

### Unit

- bps
- Kbps
- Mbps
- Gbps

---
# Latency

Latency হলো Source থেকে Destination-এ Data পৌঁছাতে যত সময় লাগে।

Latency যত কম হবে, Network তত দ্রুত অনুভূত হবে।

---

# Types of Network

| Type | Full Form | Coverage |
|------|-----------|----------|
| PAN | Personal Area Network | ১–১০ মিটার |
| LAN | Local Area Network | Room / Building |
| MAN | Metropolitan Area Network | City |
| WAN | Wide Area Network | Country / World |

### Example

- Bluetooth → PAN
- Computer Lab → LAN
- City Network → MAN
- Internet → WAN

---

# Network Topology (Introduction)

Topology হলো Network-এর Device-গুলো কীভাবে Connected আছে তার Layout।

জনপ্রিয় Topology:

- Bus
- Star
- Ring
- Mesh
- Tree

> বিস্তারিত Topology আলাদা Chapter-এ আলোচনা করা হবে।

---

# Advantages of Computer Network

- File Sharing
- Resource Sharing
- Fast Communication
- Internet Sharing
- Easy Backup
- Centralized Management

---
