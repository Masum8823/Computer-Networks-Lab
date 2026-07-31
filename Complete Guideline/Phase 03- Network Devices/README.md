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