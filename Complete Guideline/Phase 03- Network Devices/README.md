# 03. Network Devices

> [!NOTE]
> Network তৈরি, পরিচালনা এবং বিভিন্ন Device-এর মধ্যে Communication নিশ্চিত করার জন্য যে Hardware ব্যবহার করা হয়, সেগুলোকে Network Devices বলা হয়।

---

# Table of Contents

- What is a Network Device?
- NIC (Network Interface Card)
- Hub
- Switch
- Router
- Bridge
- Repeater
- Modem
- Access Point (AP)
- Gateway
- Hub vs Switch vs Router
- OSI Layer Summary
- Viva Questions
- Common Mistakes
- Quick Revision

---

# What is a Network Device?

Network Device হলো এমন Hardware যা বিভিন্ন Computer বা Network-কে একে অপরের সাথে Connect করে এবং Data আদান-প্রদান নিশ্চিত করে।

---

# 1. NIC (Network Interface Card)

## Definition

NIC (Network Interface Card) হলো এমন একটি Hardware Component যা Computer-কে Network-এর সাথে সংযুক্ত করে।

### Functions

- Network-এ Connect করে
- MAC Address বহন করে
- Data Send ও Receive করে

### Example

- Ethernet Card
- Wi-Fi Card

> [!IMPORTANT]
> প্রতিটি NIC-এর একটি Unique MAC Address থাকে।

---

# 2. Hub

## Definition

Hub হলো একটি **Layer 1 (Physical Layer)** Device।

এটি কোনো Data বুঝতে পারে না। একটি Port-এ Data আসলে সেটি সব Port-এ পাঠিয়ে দেয়।

### Characteristics

- Layer 1 Device
- Intelligent নয়
- MAC Address ব্যবহার করে না
- Broadcast করে
- Collision বেশি হয়

### Diagram

```text
      Hub
   /   |   \
 PC1  PC2  PC3
```

### Advantages

- দাম কম
- Setup সহজ

### Disadvantages

- Speed কম
- Collision বেশি
- Security কম

---

# 3. Switch

## Definition

Switch হলো **Layer 2 (Data Link Layer)** Device।

এটি MAC Address দেখে নির্দিষ্ট Device-এ Data পাঠায়।

### Characteristics

- Layer 2 Device
- MAC Address ব্যবহার করে
- Intelligent Device
- Collision কম
- Speed বেশি

### Diagram

```text
      Switch
    /    |    \
  PC1   PC2   PC3
```


### Advantages

- Fast Communication
- Security বেশি
- Collision কম

### Disadvantages

- Hub-এর তুলনায় দাম বেশি

---

# 4. Router

## Definition

Router হলো **Layer 3 (Network Layer)** Device।

এটি বিভিন্ন Network (Different LAN)-কে Connect করে এবং IP Address ব্যবহার করে Packet Forward করে।

### Characteristics

- Layer 3 Device
- IP Address ব্যবহার করে
- Routing করে
- Internet Connect করে

### Diagram

```text
LAN 1
   |
 Switch
   |
 Router
   |
 Switch
   |
LAN 2
```

### Advantages

- Different Network Connect করে
- Best Path নির্বাচন করে
- Security ভালো

---

# 5. Bridge

## Definition

Bridge হলো **Layer 2 Device**, যা দুটি LAN Segment-কে যুক্ত করে।

### Functions

- Network Traffic কমায়
- MAC Address ব্যবহার করে

---

# 6. Repeater

## Definition

Repeater হলো **Layer 1 Device**, যা দুর্বল Signal-কে পুনরায় শক্তিশালী (Regenerate) করে।

### Uses

- Long Distance Communication
- Signal Boost

---

# 7. Modem

## Definition

Modem-এর পূর্ণরূপ **Modulator-Demodulator**।

এটি Digital Signal-কে Analog Signal-এ এবং Analog Signal-কে Digital Signal-এ রূপান্তর করে।

### Uses
- ISP-এর Internet ব্যবহার করতে
- Home Broadband Connection

---

# 8. Access Point (AP)

## Definition

Access Point একটি Wireless Network Device, যা Wi-Fi-এর মাধ্যমে Device-কে Network-এ Connect করে।

### Example

- Wi-Fi Router
- Office Wireless Network

---

# 9. Gateway

## Definition

Gateway হলো এমন একটি Device, যা দুইটি ভিন্ন ধরনের Network-এর মধ্যে Communication নিশ্চিত করে।

> [!TIP]
> Lab-এ "Default Gateway" বলতে সাধারণত Router-এর IP Address-কে বোঝানো হয়।

---

# Hub vs Switch vs Router

| Feature | Hub | Switch | Router |
|----------|-----|--------|---------|
| OSI Layer | Layer 1 | Layer 2 | Layer 3 |
| Address Used | None | MAC | IP |
| Intelligent | No | Yes | Yes |
| Collision | High | Low | Very Low |
| Speed | Slow | Fast | Fast |
| Broadcast | Yes | No (Normal Data) | No |
| Connects | Same LAN | Same LAN | Different LAN |

---

# OSI Layer Summary

| Device | Layer |
|----------|-------|
| Hub | Layer 1 |
| Repeater | Layer 1 |
| Switch | Layer 2 |
| Bridge | Layer 2 |
| Router | Layer 3 |

---

# Viva Questions

### 1. NIC কী?

Computer-কে Network-এর সাথে Connect করার Hardware।

---

### 2. Hub কোন Layer-এ কাজ করে?

Layer 1 (Physical Layer)

---

### 3. Switch কোন Address ব্যবহার করে?

MAC Address

---

### 4. Router কোন Address ব্যবহার করে?

IP Address

---

### 5. Router কোন Layer-এ কাজ করে?

Layer 3 (Network Layer)

---

### 6. Repeater-এর কাজ কী?

Weak Signal পুনরায় শক্তিশালী করা।

---

### 7. Bridge-এর কাজ কী?

দুটি LAN Segment Connect করা।

---

### 8. Modem-এর পূর্ণরূপ কী?

Modulator-Demodulator

---

### 9. Access Point কী?

Wireless Network প্রদানকারী Device।

---

### 10. Default Gateway কী?

Router-এর IP Address।

---

# Common Mistakes

> [!WARNING]
> Hub এবং Switch এক জিনিস নয়।

> [!WARNING]
> Router MAC Address দেখে Packet Forward করে না, IP Address দেখে।

> [!WARNING]
> Switch Different LAN Connect করতে পারে না।

---

# Quick Revision

- NIC = Connects Computer to Network
- Hub = Layer 1 = Broadcast
- Switch = Layer 2 = MAC Address
- Router = Layer 3 = IP Address
- Bridge = Connects LAN Segments
- Repeater = Signal Boost
- Modem = Digital ↔ Analog
- Access Point = Wi-Fi
- Gateway = Connects Different Networks
- Default Gateway = Router IP

---

# Exam Tips

> [!TIP]
> Viva-তে সবচেয়ে বেশি জিজ্ঞেস করা হয়:
>
> - Hub vs Switch
> - Switch vs Router
> - Router কোন Layer?
> - MAC Address কে ব্যবহার করে?
> - IP Address কে ব্যবহার করে?

> [!IMPORTANT]
> শুধু Definition মুখস্থ করো না। প্রতিটি Device-এর **কাজ (Function)** এবং **OSI Layer**-ও মনে রাখবে।