# 08. Dynamic Routing using RIP

> [!NOTE]
> RIP (Routing Information Protocol) হলো একটি **Dynamic Routing Protocol**। এটি Router-কে স্বয়ংক্রিয়ভাবে Route শিখতে সাহায্য করে।

---

# Table of Contents

- What is Routing?
- Static vs Dynamic Routing
- What is RIP?
- Features of RIP
- Hop Count
- How RIP Works
- Network Topology
- RIP Configuration
- Verification Commands
- Advantages
- Disadvantages
- Common Errors
- Viva Questions
- Quick Revision

---
# What is Routing?

**Routing** হলো একটি Network থেকে অন্য Network-এ Data পাঠানোর জন্য সঠিক পথ (Route) নির্বাচন করার প্রক্রিয়া।

Router এই কাজটি করে।

Example

```text
PC → Switch → Router → Switch → PC
```

---

# Static Routing vs Dynamic Routing

| Static Routing | Dynamic Routing |
|---------------|-----------------|
| Route নিজে লিখতে হয় | Route নিজে নিজে শেখে |
| ছোট Network | বড় Network |
| কম Flexible | বেশি Flexible |
| Manual | Automatic |

> [!IMPORTANT]
> **Static Routing = Manual**
>
> **Dynamic Routing = Automatic**

---
# What is RIP?

**RIP (Routing Information Protocol)** হলো একটি Dynamic Routing Protocol।

এটি Router-দের মধ্যে Routing Information Exchange করে।

---