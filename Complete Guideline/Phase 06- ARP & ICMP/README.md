# 06. ARP & ICMP

> [!NOTE]
> ARP এবং ICMP হলো Network Communication-এর দুটি গুরুত্বপূর্ণ Protocol। Packet Tracer-এর Simulation Mode-এ এগুলোর Packet Flow দেখা যায়।

---

# Table of Contents

- What is ARP?
- Why ARP is Needed?
- How ARP Works
- ARP Request
- ARP Reply
- ARP Cache
- What is ICMP?
- Ping
- Tracert
- ARP vs ICMP
- Packet Flow
- Viva Questions
- Common Mistakes
- Quick Revision

---
# What is ARP?

**ARP (Address Resolution Protocol)** এমন একটি Protocol যা **IP Address থেকে MAC Address খুঁজে বের করে।**

> [!IMPORTANT]
> **ARP = IP → MAC**

Example:

```text
IP Address

192.168.1.10

↓

MAC Address

00:1A:2B:3C:4D:5E
```

---

# Why ARP is Needed?

Switch Data Forward করার জন্য **MAC Address** ব্যবহার করে।

কিন্তু আমরা সাধারণত জানি **IP Address**।

তাই Communication শুরু হওয়ার আগে IP থেকে MAC বের করতে ARP ব্যবহার করা হয়।

---