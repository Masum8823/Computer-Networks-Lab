# 02. Cisco Packet Tracer Basics

> [!NOTE]
> Cisco Packet Tracer হলো Cisco-এর তৈরি একটি Network Simulation Software। এটি ব্যবহার করে বাস্তব Network তৈরি, Configure এবং Test করা যায়।

---

# Table of Contents

- What is Cisco Packet Tracer?
- Why Do We Use Packet Tracer?
- Packet Tracer Interface
- Device Categories
- End Devices
- Network Devices
- Connection Types
- Cable Types
- Realtime Mode
- Simulation Mode
- Creating Your First Network
- Basic IP Configuration
- Testing Connection
- Common Errors
- Viva Questions
- Quick Revision

---

# What is Cisco Packet Tracer?

**Cisco Packet Tracer** হলো একটি **Network Simulation Software**, যেখানে বাস্তব Router, Switch, PC ইত্যাদি ব্যবহার না করেও Virtual Network তৈরি করা যায়।

### Developed By

- Cisco Systems

### Used For

- Learning Networking
- CCNA Practice
- Network Design
- Network Simulation
- Lab Practice

---

# Why Do We Use Packet Tracer?

Packet Tracer ব্যবহারের প্রধান কারণগুলো—

- Network Design করা
- Router Configure করা
- Switch Configure করা
- IP Configuration শেখা
- Ping Test করা
- Routing Practice করা
- Lab Practice করা

> [!TIP]
> বাস্তব Network Device ছাড়াই Lab Practice করার জন্য Packet Tracer সবচেয়ে জনপ্রিয় Software।

---
# Packet Tracer Interface

Packet Tracer খুললে প্রধানত নিচের অংশগুলো দেখা যায়।

- Menu Bar
- Toolbar
- Workspace
- Device List
- Device Specific Selection
- Realtime Mode
- Simulation Mode

---

# Workspace

Workspace হলো যেখানে আমরা Network Design করি।

দুই ধরনের Workspace আছে।

## 1. Logical Workspace

এখানে Logical Network তৈরি করা হয়।

এই Workspace-ই Lab-এ সবচেয়ে বেশি ব্যবহার করা হয়।

---

## 2. Physical Workspace

এখানে বাস্তব Room বা Building অনুযায়ী Network Layout দেখা যায়।

---

# Device Categories

Packet Tracer-এ বিভিন্ন ধরনের Device পাওয়া যায়।

- Network Devices
- End Devices
- Connections
- Wireless Devices

---
# End Devices

End Device হলো যেসব Device User সরাসরি ব্যবহার করে।

### Example

- PC
- Laptop
- Server
- Printer
- IP Phone

---
# Network Devices

Network তৈরির জন্য যেসব Device ব্যবহার করা হয়।

### Example

- Hub
- Switch
- Router
- Access Point

---
# Connection Types

Packet Tracer-এ Devices Connect করার জন্য বিভিন্ন Cable ব্যবহার করা হয়।

সবচেয়ে গুরুত্বপূর্ণ Cable ৪টি।

---

## 1. Copper Straight-Through Cable

### ব্যবহার

Different Devices Connect করতে।

### Example

- PC ↔ Switch
- Switch ↔ Router

---

## 2. Copper Cross-Over Cable

### ব্যবহার

Same Type Device Connect করতে।

### Example

- PC ↔ PC
- Switch ↔ Switch
- Router ↔ Router

> [!IMPORTANT]
> তোমাদের Lab-এ Peer-to-Peer Network-এর জন্য সাধারণত Cross-Over Cable ব্যবহার করা হয়।

---

## 3. Console Cable

Router বা Switch Configure করার জন্য ব্যবহার করা হয়।

### Example

PC ↔ Router Console Port

---

## 4. Fiber Cable

Long Distance এবং High Speed Communication-এর জন্য ব্যবহার করা হয়।

---

# Realtime Mode

Realtime Mode-এ Network Live অবস্থায় কাজ করে।

সব Configuration সাথে সাথে কার্যকর হয়।

---
# Simulation Mode

Simulation Mode-এ Packet কীভাবে এক Device থেকে অন্য Device-এ যায়, তা Step by Step দেখা যায়।

এটি ARP, ICMP, RIP ইত্যাদি বোঝার জন্য খুবই গুরুত্বপূর্ণ।

---

# Creating Your First Network

ধাপ ১

একটি PC নাও।

ধাপ ২

একটি Switch নাও।

ধাপ ৩

Copper Straight-Through Cable দিয়ে Connect করো।

```text
PC -------- Switch
```

---
# Basic IP Configuration

PC-তে ক্লিক করো।

Desktop → IP Configuration

তারপর—

```text
IP Address : 192.168.1.10

Subnet Mask : 255.255.255.0

Gateway : 192.168.1.1
```

---

# Testing Connection

Command Prompt খুলে লিখো—

```bash
ping 192.168.1.1
```

যদি নিচের মতো Reply আসে—

```text
Reply from 192.168.1.1
```

তাহলে Connection Successful।

---

# Realtime vs Simulation

| Realtime | Simulation |
|-----------|------------|
| Live Communication | Step-by-Step Communication |
| দ্রুত কাজ করে | Packet Flow দেখায় |
| সাধারণ Lab | শেখার জন্য বেশি উপযোগী |

---