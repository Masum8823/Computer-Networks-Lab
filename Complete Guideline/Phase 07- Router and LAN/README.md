# 07. Connecting Different LAN Using Router

> [!NOTE]
> একটি Router ব্যবহার করে দুই বা ততোধিক ভিন্ন Network (LAN)-কে একে অপরের সাথে যুক্ত করা যায়।

---

# Table of Contents

- What is a Router?
- Why Do We Need a Router?
- Same LAN vs Different LAN
- Router Interfaces
- Default Gateway
- Basic Network Diagram
- Router Configuration
- PC Configuration
- Testing the Network
- Common Errors
- Viva Questions
- Quick Revision

---

# What is a Router?

**Router** হলো একটি **Layer 3 (Network Layer)** Device, যা **IP Address** ব্যবহার করে এক Network থেকে অন্য Network-এ Data পাঠায়।

### Main Functions

- Different LAN Connect করা
- Best Path নির্বাচন করা
- Packet Forward করা
- Internet-এর সাথে সংযোগ দেওয়া

> [!IMPORTANT]
> Router **MAC Address নয়**, **IP Address** দেখে Packet Forward করে।

---

# Why Do We Need a Router?

একই Network-এর Device-গুলো Switch দিয়ে যোগাযোগ করতে পারে।

কিন্তু যদি দুইটি Device **Different Network**-এ থাকে, তাহলে Router ছাড়া তারা যোগাযোগ করতে পারবে না।

### Example

```text
PC0 → 192.168.1.10

PC1 → 192.168.2.10
```

এরা Different Network-এ আছে।

তাই Router দরকার।

---