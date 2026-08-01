# 04. IP Addressing

> [!NOTE]
> IP Address হলো Computer Networks-এর সবচেয়ে গুরুত্বপূর্ণ Topic। ARP, Router, Ping, Routing—সবকিছুর ভিত্তি হলো IP Address।

---

# Table of Contents

- What is an IP Address?
- Why Do We Need an IP Address?
- IPv4
- IPv6
- IPv4 Structure
- Network ID
- Host ID
- Subnet Mask
- Default Gateway
- Public IP
- Private IP
- Private IP Ranges
- Loopback Address
- APIPA
- IP Classes
- Network Address
- Broadcast Address
- Usable Host Address
- MAC Address vs IP Address
- Viva Questions
- Common Mistakes
- Quick Revision

---
# What is an IP Address?

**IP (Internet Protocol) Address** হলো একটি **Logical Address**, যা Network-এর প্রতিটি Device-কে আলাদাভাবে শনাক্ত (Identify) করতে ব্যবহৃত হয়।

### Example

```text
192.168.1.10
```

---

# Why Do We Need an IP Address?

IP Address ব্যবহার করা হয়—

- Device Identify করতে
- Data সঠিক Destination-এ পাঠাতে
- Network Communication করতে

> [!IMPORTANT]
> IP Address ছাড়া Router কোনো Device-এ Packet পাঠাতে পারে না।

---
# IPv4

IPv4-এর পূর্ণরূপ **Internet Protocol Version 4**।

### Features

- 32-bit Address
- 4 Octets
- Decimal Format

Example

```text
192.168.1.10
```

---
# IPv6

IPv6-এর পূর্ণরূপ **Internet Protocol Version 6**।

### Features

- 128-bit Address
- Hexadecimal Format
- IPv4-এর তুলনায় অনেক বেশি Address Support করে

Example

```text
2001:0db8:85a3::8a2e:0370:7334
```

---

# IPv4 Structure

```text
192 . 168 . 1 . 10
 │     │     │    │
Octet Octet Octet Octet
```

প্রতিটি Octet-এর Range:

```text
0 – 255
```

---