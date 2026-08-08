# 🔀 Connecting Multiple Subnets using Static Routing (Packet Tracer Lab)

> এই নোটটা আমার CN (Computer Networking) Lab এর কাজ থেকে বানানো — **দুইটা Router ব্যবহার করে তিনটা আলাদা LAN connect করা এবং Static Routing configure করার ধাপে ধাপে guideline।** পরে যেকোনো সময় চোখ বুলিয়ে পুরো setup সহজেই মনে করে নেওয়া যাবে।

---

## Connection in Cisco Packet Tracer:



---

## 📑 Table of Contents

| #  | Section                                                               | Link |
| -- | --------------------------------------------------------------------- | ---- |
| 1  | [Overview](#1️⃣-overview)                                             |      |
| 2  | [Physical Setup (Devices)](#2️⃣-physical-setup-devices-বসানো)         |      |
| 3  | [Cabling](#3️⃣-cabling-তার-দিয়ে-কানেক্ট-করা)                         |      |
| 4  | [IP Planning](#4️⃣-ip-planning)                                       |      |
| 5  | [PC Configuration](#5️⃣-pc-configuration)                             |      |
| 6  | [Router Interface Configuration](#6️⃣-router-interface-configuration) |      |
| 7  | [Static Route Configuration](#7️⃣-static-route-configuration)         |      |
| 8  | [Verify Routing Table](#8️⃣-verify-routing-table)                     |      |
| 9  | [Testing the Connection](#9️⃣-testing-the-connection)                 |      |
| 10 | [Packet Flow](#🔟-packet-flow)                                        |      |
| 11 | [Quick Reference Table](#1️⃣1️⃣-quick-reference-table)                |      |
| 12 | [Common Mistakes / Tips](#1️⃣2️⃣-common-mistakes--tips)               |      |

---

# 1️⃣ Overview

এই lab-এ **৩টা আলাদা LAN** কে **২টা Router** ব্যবহার করে connect করা হবে।

Router 1-এর সাথে দুইটা LAN থাকবে এবং Router 4-এর সাথে একটা LAN থাকবে। দুই Router-এর মধ্যে একটা **WAN link** থাকবে।

সব network-এর মধ্যে communication enable করার জন্য manually **Static Route** configure করতে হবে।

```text
              LAN 1
         192.168.1.0/24

      PC0    PC1    PC2
       |      |      |
       +------+------+
              |
           Switch0
              |
          Gi0/0
        192.168.1.1
              |
         +---------+
         | Router1 |
         +---------+
          Gi0/2
        192.168.2.1
              |
           Switch1
           /     \
         PC3     PC4
         
          Gi0/1
        10.10.0.1
              |
              |
         WAN Link
       10.10.0.0/24
              |
              |
        10.10.0.2
          Gi0/0
         +---------+
         | Router4 |
         +---------+
          Gi0/1
        192.168.3.1
              |
           Switch2
           /     \
         PC5     PC6

              LAN 3
       192.168.3.0/24
```

### Main Idea

```text
LAN 1 ─┐
       ├── Router 1 ─── Router 4 ─── LAN 3
LAN 2 ─┘
```

Router 1 এবং Router 4-এর মধ্যে communication-এর জন্য **10.10.0.0/24** network ব্যবহার করা হয়েছে।

---

# 2️⃣ Physical Setup (Devices বসানো)

Cisco Packet Tracer-এ নিচের devices গুলো place করো:

### Routers

**Network Devices → Routers**

* Router 1 → `2911` / `4331`
* Router 4 → `2911` / `4331`

### Switches

**Network Devices → Switches**

* Switch0
* Switch1
* Switch2

### PCs

**End Devices → PC**

মোট **৭টা PC**:

* LAN 1 → PC0, PC1, PC2
* LAN 2 → PC3, PC4
* LAN 3 → PC5, PC6

---

# 3️⃣ Cabling (তার দিয়ে কানেক্ট করা)

**Connections** থেকে প্রয়োজন অনুযায়ী cable select করো।

## LAN 1

```text
PC0 → Switch0
PC1 → Switch0
PC2 → Switch0
Switch0 → Router1 GigabitEthernet 0/0
```

## LAN 2

```text
PC3 → Switch1
PC4 → Switch1
Switch1 → Router1 GigabitEthernet 0/2
```

## LAN 3

```text
PC5 → Switch2
PC6 → Switch2
Switch2 → Router4 GigabitEthernet 0/1
```

## Router-to-Router

```text
Router1 Gig0/1 → Router4 Gig0/0
```

Router-to-Router connection-এর জন্য topology অনুযায়ী **Copper Cross-Over অথবা Serial cable** ব্যবহার করা যেতে পারে।

> ⚠️ **নোট:** Router interface configure করার আগে interface-এর light **Red** থাকতে পারে। Interface configure করে `no shutdown` দিলে link **Green** হবে।

---

# 4️⃣ IP Planning

এখানে মোট **৩টা LAN network** এবং **১টা WAN network** ব্যবহার করা হয়েছে।

| Network | Network Address  | Gateway                 |
| ------- | ---------------- | ----------------------- |
| LAN 1   | `192.168.1.0/24` | `192.168.1.1`           |
| LAN 2   | `192.168.2.0/24` | `192.168.2.1`           |
| LAN 3   | `192.168.3.0/24` | `192.168.3.1`           |
| WAN     | `10.10.0.0/24`   | `10.10.0.1 / 10.10.0.2` |

### সহজভাবে মনে রাখো

```text
LAN 1 → 192.168.1.x
LAN 2 → 192.168.2.x
LAN 3 → 192.168.3.x

WAN → 10.10.0.x
```

---

# 5️⃣ PC Configuration

প্রতিটা PC-তে:

```text
PC → Desktop → IP Configuration
```

তারপর IP Address, Subnet Mask এবং Default Gateway set করো।

---

## 🖥️ LAN 1

| PC  | IP Address    | Subnet Mask     | Default Gateway |
| --- | ------------- | --------------- | --------------- |
| PC0 | `192.168.1.2` | `255.255.255.0` | `192.168.1.1`   |
| PC1 | `192.168.1.3` | `255.255.255.0` | `192.168.1.1`   |
| PC2 | `192.168.1.4` | `255.255.255.0` | `192.168.1.1`   |

---

## 🖥️ LAN 2

| PC  | IP Address    | Subnet Mask     | Default Gateway |
| --- | ------------- | --------------- | --------------- |
| PC3 | `192.168.2.2` | `255.255.255.0` | `192.168.2.1`   |
| PC4 | `192.168.2.3` | `255.255.255.0` | `192.168.2.1`   |

---

## 🖥️ LAN 3

| PC  | IP Address    | Subnet Mask     | Default Gateway |
| --- | ------------- | --------------- | --------------- |
| PC5 | `192.168.3.2` | `255.255.255.0` | `192.168.3.1`   |
| PC6 | `192.168.3.3` | `255.255.255.0` | `192.168.3.1`   |

> ⚠️ **Default Gateway খুব important।** যে LAN-এ PC আছে, সেই LAN-এর router interface-এর IP Gateway হিসেবে দিতে হবে।

---

# 6️⃣ Router Interface Configuration

এবার Router-এর interface-গুলোতে IP address দিতে হবে।

Router-এ click করে:

```text
CLI
```

select করো।

---

## 🔵 Router 1 Configuration

Router 1-এর তিনটা interface configure করতে হবে।

### GigabitEthernet 0/0

```bash
Router1> enable
Router1# configure terminal

Router1(config)# interface gigabitEthernet 0/0
Router1(config-if)# ip address 192.168.1.1 255.255.255.0
Router1(config-if)# no shutdown
```

এটা **LAN 1-এর Gateway**।

---

### GigabitEthernet 0/2

```bash
Router1(config)# interface gigabitEthernet 0/2
Router1(config-if)# ip address 192.168.2.1 255.255.255.0
Router1(config-if)# no shutdown
```

এটা **LAN 2-এর Gateway**।

---

### GigabitEthernet 0/1

```bash
Router1(config)# interface gigabitEthernet 0/1
Router1(config-if)# ip address 10.10.0.1 255.255.255.0
Router1(config-if)# no shutdown
```

এটা Router 1-এর **WAN-side IP**।

---

# 🔴 Router 4 Configuration

Router 4-এর দুইটা interface configure করতে হবে।

### GigabitEthernet 0/0

```bash
Router4> enable
Router4# configure terminal

Router4(config)# interface gigabitEthernet 0/0
Router4(config-if)# ip address 10.10.0.2 255.255.255.0
Router4(config-if)# no shutdown
```

এটা Router 4-এর **WAN-side IP**।

---

### GigabitEthernet 0/1

```bash
Router4(config)# interface gigabitEthernet 0/1
Router4(config-if)# ip address 192.168.3.1 255.255.255.0
Router4(config-if)# no shutdown
```

এটা **LAN 3-এর Gateway**।

---

# 7️⃣ Static Route Configuration

এটাই এই Lab-এর **main part**।

Router নিজে শুধু তার **directly connected network** সম্পর্কে জানে।

যে network directly connected না, সেই network-এ যাওয়ার জন্য router-কে manually route বলে দিতে হবে।

এই কাজটাই **Static Routing**।

---

## 🟢 Router 1-এ Static Route

Router 1 directly connected:

```text
192.168.1.0/24
192.168.2.0/24
10.10.0.0/24
```

কিন্তু Router 1-এর কাছে **LAN 3** directly connected না।

LAN 3:

```text
192.168.3.0/24
```

তাই Router 1-এ এই route দিতে হবে:

```bash
Router1(config)# ip route 192.168.3.0 255.255.255.0 10.10.0.2
```

### সহজভাবে:

```text
Destination Network
        ↓
192.168.3.0/24

Next Hop
        ↓
10.10.0.2
        ↓
Router 4
```

অর্থাৎ:

> **192.168.3.0 network-এ যেতে হলে Router 4-এর দিকে পাঠাও।**

---

## 🔴 Router 4-এ Static Routes

Router 4 directly connected:

```text
192.168.3.0/24
10.10.0.0/24
```

কিন্তু Router 4-এর কাছে:

```text
192.168.1.0/24
192.168.2.0/24
```

directly connected না।

তাই Router 4-এ **দুইটা static route** দিতে হবে।

### Route to LAN 1

```bash
Router4(config)# ip route 192.168.1.0 255.255.255.0 10.10.0.1
```

### Route to LAN 2

```bash
Router4(config)# ip route 192.168.2.0 255.255.255.0 10.10.0.1
```

### সহজভাবে:

```text
192.168.1.0/24 → Router 1
192.168.2.0/24 → Router 1
```

Next-hop:

```text
10.10.0.1
```

---

# 8️⃣ Verify Routing Table

Static route ঠিকভাবে add হয়েছে কিনা দেখতে:

```bash
show ip route
```

Router 1 এবং Router 4 — দুই জায়গাতেই command-টা চালাও।

Static route সাধারণত:

```text
S
```

দিয়ে দেখাবে।

উদাহরণ:

```text
S    192.168.3.0/24 [1/0] via 10.10.0.2
```

এখানে:

```text
S        → Static Route
192.168.3.0/24 → Destination Network
10.10.0.2 → Next-Hop IP
```

---

# 9️⃣ Testing the Connection

Configuration শেষ হলে communication test করতে হবে।

## Method 1 — Simple PDU

ডান পাশের toolbar থেকে **Add Simple PDU** select করো।

তারপর:

```text
PC0 → PC6
```

দাও।

অর্থাৎ:

```text
192.168.1.2 → 192.168.3.3
```

নিচে যদি:

```text
Successful
```

দেখায়, তাহলে communication successful।

> 💡 প্রথমবার `Failed` আসতে পারে কারণ ARP-এর মাধ্যমে MAC address resolve হতে কিছু সময় লাগে। আবার PDU পাঠালে সাধারণত `Successful` হবে।

---

## Method 2 — Ping

PC0-তে click করো:

```text
Desktop → Command Prompt
```

তারপর:

```bash
ping 192.168.3.3
```

যদি এমন reply পাও:

```text
Reply from 192.168.3.3
```

তাহলে বুঝবে PC0 থেকে PC6 পর্যন্ত connectivity successfully established হয়েছে।

---

# 🔟 Packet Flow

ধরা যাক:

```text
PC0 → PC6
```

অর্থাৎ:

```text
192.168.1.2 → 192.168.3.3
```

Packet-এর path হবে:

```text
PC0
192.168.1.2
   ↓
Router 1
192.168.1.1
   ↓
10.10.0.1
   ↓
10.10.0.2
   ↓
Router 4
192.168.3.1
   ↓
PC6
192.168.3.3
```

### সহজভাবে:

```text
PC0
 ↓
Router 1
 ↓
WAN
 ↓
Router 4
 ↓
PC6
```

---

# 🔁 Return Path কেন Important?

ধরো PC0 থেকে PC6-এ packet গেল:

```text
PC0 → Router 1 → Router 4 → PC6
```

PC6 যদি reply পাঠায়, তাহলে reply-কে আবার ফিরে আসতে হবে:

```text
PC6 → Router 4 → Router 1 → PC0
```

এই কারণে Router 4-এ LAN 1 এবং LAN 2-এর route configure করা হয়েছে:

```bash
ip route 192.168.1.0 255.255.255.0 10.10.0.1

ip route 192.168.2.0 255.255.255.0 10.10.0.1
```

> ⚠️ **Forward path থাকলেই হবে না, Return path-ও থাকতে হবে।**

---

# 1️⃣1️⃣ Quick Reference Table

## PC Configuration

| Device | IP Address    | Gateway       |
| ------ | ------------- | ------------- |
| PC0    | `192.168.1.2` | `192.168.1.1` |
| PC1    | `192.168.1.3` | `192.168.1.1` |
| PC2    | `192.168.1.4` | `192.168.1.1` |
| PC3    | `192.168.2.2` | `192.168.2.1` |
| PC4    | `192.168.2.3` | `192.168.2.1` |
| PC5    | `192.168.3.2` | `192.168.3.1` |
| PC6    | `192.168.3.3` | `192.168.3.1` |

---

## Router Interface

| Router   | Interface | IP Address    | Purpose |
| -------- | --------- | ------------- | ------- |
| Router 1 | Gi0/0     | `192.168.1.1` | LAN 1   |
| Router 1 | Gi0/2     | `192.168.2.1` | LAN 2   |
| Router 1 | Gi0/1     | `10.10.0.1`   | WAN     |
| Router 4 | Gi0/0     | `10.10.0.2`   | WAN     |
| Router 4 | Gi0/1     | `192.168.3.1` | LAN 3   |

---

## Static Routes

### Router 1

```bash
ip route 192.168.3.0 255.255.255.0 10.10.0.2
```

### Router 4

```bash
ip route 192.168.1.0 255.255.255.0 10.10.0.1

ip route 192.168.2.0 255.255.255.0 10.10.0.1
```

---

# 1️⃣2️⃣ Common Mistakes / Tips

* ❌ PC-এর **Default Gateway** ভুল দিলে অন্য network-এ communication হবে না।
* ❌ Router interface-এ `no shutdown` দিতে ভুলে গেলে interface **Red** থাকবে।
* ❌ দুইটা LAN-এ একই network address ব্যবহার করা যাবে না।
* ❌ Static route-এ ভুল **Destination Network** দিলে packet সঠিক জায়গায় যাবে না।
* ❌ Static route-এ ভুল **Next-Hop IP** দিলে routing fail করবে।
* ❌ শুধু forward route দিলেই হবে না — **return route**-ও configure করতে হবে।
* ❌ Router-to-Router WAN interface-এর IP একই network-এর হতে হবে।
* ✅ সব PC-এর subnet mask সঠিকভাবে `255.255.255.0` রাখো।
* ✅ Router-এর interface IP-ই সেই LAN-এর **Default Gateway** হবে।
* ✅ `show ip route` দিয়ে routing table check করো।
* ✅ প্রথমবার Ping/PDU fail করলে panic করার দরকার নেই; ARP resolve হওয়ার পর আবার test করো।

---

# 🧠 Quick Revision

এই Lab-এর পুরো concept এক লাইনে:

```text
3 LANs
   ↓
2 Routers
   ↓
WAN Link
   ↓
Static Routes
   ↓
Inter-Network Communication
```

### মনে রাখার মতো ৩টা জিনিস:

```text
1. IP Address ঠিক হতে হবে
2. Default Gateway ঠিক হতে হবে
3. দুই পাশেই Proper Static Route থাকতে হবে
```

### সবচেয়ে important commands:

```bash
no shutdown
```

```bash
ip route
```

```bash
show ip route
```

```bash
ping <destination-ip>
```

---

## ✅ Final Checklist

Lab শেষ করার আগে check করো:

* [ ] 2টি Router আছে
* [ ] 3টি Switch আছে
* [ ] 7টি PC আছে
* [ ] সব PC-তে IP Address configured
* [ ] সব PC-তে Default Gateway configured
* [ ] Router interfaces-এর IP configured
* [ ] সব Router interface `no shutdown` করা হয়েছে
* [ ] Router 1 → LAN 3-এর static route configured
* [ ] Router 4 → LAN 1-এর static route configured
* [ ] Router 4 → LAN 2-এর static route configured
* [ ] `show ip route` দিয়ে routes verified
* [ ] `PC0 → PC6` ping successful
* [ ] Simple PDU successful

---

# 🎯 Final Result

```text
PC0 (192.168.1.2)
        ↓
   Router 1
        ↓
  10.10.0.0/24
        ↓
   Router 4
        ↓
PC6 (192.168.3.3)

        ✅ SUCCESS
```

**Static Routing successfully configured and communication established between multiple subnets.**
