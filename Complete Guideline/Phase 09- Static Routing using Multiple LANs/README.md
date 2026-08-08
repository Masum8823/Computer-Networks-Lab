# 09. Connecting Multiple Subnets using Static Routing

> [!NOTE]
> **Static Routing** হলো এমন একটি routing method যেখানে Administrator manually Router-এর Routing Table-এ route configure করে দেয়।
>
> এই lab-এ **2টি Router এবং 3টি আলাদা LAN** ব্যবহার করে Static Routing-এর মাধ্যমে multiple subnet-এর মধ্যে communication establish করা হয়েছে।

---

# Table of Contents

* [Overview](#overview)
* [What is Routing?](#what-is-routing)
* [What is Static Routing?](#what-is-static-routing)
* [Network Topology](#network-topology)
* [IP Planning](#ip-planning)
* [IP Addressing Table](#ip-addressing-table)
* [Physical Setup](#physical-setup)
* [Cabling](#cabling)
* [PC Configuration](#pc-configuration)
* [Router Interface Configuration](#router-interface-configuration)
* [What is a Static Route?](#what-is-a-static-route)
* [Static Route Configuration](#static-route-configuration)
* [How Static Routing Works](#how-static-routing-works)
* [Verify Routing Table](#verify-routing-table)
* [Testing Connectivity](#testing-connectivity)
* [Communication Flow](#communication-flow)
* [Advantages](#advantages)
* [Disadvantages](#disadvantages)
* [Common Errors](#common-errors)
* [Troubleshooting Checklist](#troubleshooting-checklist)
* [Quick Reference](#quick-reference)
* [Viva Questions](#viva-questions)
* [Quick Revision](#quick-revision)
* [Exam Tips](#exam-tips)

---

# Overview

এই lab-এ **দুইটি Router** ব্যবহার করে **তিনটি আলাদা LAN/Subnet** connect করা হয়েছে।

Topology-তে:

* Router 1-এর সাথে LAN 1 এবং LAN 2 connected।
* Router 4-এর সাথে LAN 3 connected।
* Router 1 এবং Router 4 একটি WAN link-এর মাধ্যমে connected।
* দুই Router-এর মধ্যে **Static Route** configure করা হয়েছে।
* এরপর এক LAN থেকে অন্য LAN-এ `ping` এবং **Simple PDU** ব্যবহার করে connectivity test করা হয়েছে।

---

# What is Routing?

**Routing** হলো একটি network থেকে অন্য network-এ data packet পাঠানোর জন্য appropriate path নির্বাচন করার process।

Router Routing Table ব্যবহার করে destination network অনুযায়ী packet forward করে।

Example:

```text
PC
 ↓
Switch
 ↓
Router
 ↓
Another Router
 ↓
Switch
 ↓
PC
```

---

# What is Static Routing?

**Static Routing** হলো একটি routing method যেখানে Administrator manually Router-এর Routing Table-এ route configure করে।

Static Route সাধারণত এই format-এ configure করা হয়:

```bash
ip route <destination-network> <subnet-mask> <next-hop-ip>
```

Example:

```bash
ip route 192.168.3.0 255.255.255.0 10.10.0.2
```

এর অর্থ:

> `192.168.3.0/24` network-এ যেতে হলে packet-কে `10.10.0.2` Router-এর দিকে পাঠাতে হবে।

---

# Static Routing-এর মূল ধারণা

```text
Source Network
      ↓
Router
      ↓
Next-Hop Router
      ↓
Destination Network
```

Static Routing-এ Router নিজে থেকে remote network শেখে না।

Administrator-কে manually route define করতে হয়।

> [!IMPORTANT]
> **Static Routing = Manual Route Configuration**

---

# Network Topology

```text
                         WAN
                    10.10.0.0/24
                          
      LAN 1                  LAN 2
  192.168.1.0/24         192.168.2.0/24
       |                       |
      PCs                     PCs
       |                       |
    Switch                  Switch
       |                       |
       +------ Router 1 -------+
                   |
                   |
              10.10.0.1
                   |
                   |
              10.10.0.2
                   |
               Router 4
                   |
                   |
                Switch
                   |
                PC5, PC6
                   
             LAN 3
         192.168.3.0/24
```

### Simple View

```text
PC0 ─┐
PC1 ─┼─ Switch ── Router 1 ───── Router 4 ── Switch ── PC5
PC2 ─┘             │     WAN        │                    PC6
                   │                │
                  LAN 2            LAN 3
                   │
              PC3, PC4
```

---

# IP Planning

এই lab-এ মোট **4টি network** ব্যবহার করা হয়েছে:

1. LAN 1
2. LAN 2
3. LAN 3
4. WAN Link

---

## LAN 1

```text
Network Address : 192.168.1.0/24
Gateway         : 192.168.1.1
```

---

## LAN 2

```text
Network Address : 192.168.2.0/24
Gateway         : 192.168.2.1
```

---

## LAN 3

```text
Network Address : 192.168.3.0/24
Gateway         : 192.168.3.1
```

---

## WAN Link

```text
Network : 10.10.0.0
Router 1: 10.10.0.1
Router 4: 10.10.0.2
```

> [!NOTE]
> WAN network-এর দুই Router interface একই subnet-এর হতে হবে।

---