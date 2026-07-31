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
