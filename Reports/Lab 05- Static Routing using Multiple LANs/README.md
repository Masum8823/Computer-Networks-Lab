# Lab 05: Establishing Connectivity Between Multiple Subnets Using Static Routing

## Overview

In this lab, we connected **three different Local Area Networks (LANs)** using **two routers** in Cisco Packet Tracer.

Each LAN was assigned a different IP network. The two routers were connected through a **WAN link**, and **Static Routing** was configured manually so that devices from different networks could communicate with each other.

This lab demonstrates how routers forward packets between remote networks using manually configured static routes.

---

# Objectives

* Create multiple LANs using switches and routers.
* Configure static IP addresses for end devices.
* Assign appropriate Default Gateways to PCs.
* Configure router interfaces with IP addresses.
* Connect two routers using a WAN link.
* Configure **Static Routes** manually.
* Verify end-to-end connectivity using `ping` and simulation tools.
* Understand the importance of a **return path** in static routing.

---

# Required Devices

| Device                           |    Quantity |
| -------------------------------- | ----------: |
| Router (2911 / 4331)             |           2 |
| Switch (2960)                    |           3 |
| PC                               |           7 |
| Copper Straight-Through Cable    | As Required |
| Copper Cross-Over / Serial Cable | As Required |

---

# Network Topology

```text
                    LAN 1
             192.168.1.0/24

        PC0       PC1       PC2
         |         |         |
         +---------+---------+
                   |
                Switch0
                   |
                Gi0/0
              192.168.1.1
                   |
                   |
              +----------+
              | Router 1 |
              +----------+
                Gi0/2
             192.168.2.1
                   |
                Switch1
               /       \
             PC3       PC4


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
              +----------+
              | Router 4 |
              +----------+
                Gi0/1
             192.168.3.1
                   |
                Switch2
               /       \
             PC5       PC6

                    LAN 3
             192.168.3.0/24
```

---

# Network Planning

The network consists of **three LANs** connected through two routers.

## LAN 1

| Network | 192.168.1.0/24 |
| ------- | -------------- |
| Gateway | 192.168.1.1    |

---

## LAN 2

| Network | 192.168.2.0/24 |
| ------- | -------------- |
| Gateway | 192.168.2.1    |

---

## LAN 3

| Network | 192.168.3.0/24 |
| ------- | -------------- |
| Gateway | 192.168.3.1    |

---

## WAN Link

| Network  | 10.10.0.0/24 |
| -------- | ------------ |
| Router 1 | 10.10.0.1    |
| Router 4 | 10.10.0.2    |

---

# IP Addressing Table

## LAN 1

| Device | IP Address  | Subnet Mask   | Default Gateway |
| ------ | ----------- | ------------- | --------------- |
| PC0    | 192.168.1.2 | 255.255.255.0 | 192.168.1.1     |
| PC1    | 192.168.1.3 | 255.255.255.0 | 192.168.1.1     |
| PC2    | 192.168.1.4 | 255.255.255.0 | 192.168.1.1     |

---

## LAN 2

| Device | IP Address  | Subnet Mask   | Default Gateway |
| ------ | ----------- | ------------- | --------------- |
| PC3    | 192.168.2.2 | 255.255.255.0 | 192.168.2.1     |
| PC4    | 192.168.2.3 | 255.255.255.0 | 192.168.2.1     |

---

## LAN 3

| Device | IP Address  | Subnet Mask   | Default Gateway |
| ------ | ----------- | ------------- | --------------- |
| PC5    | 192.168.3.2 | 255.255.255.0 | 192.168.3.1     |
| PC6    | 192.168.3.3 | 255.255.255.0 | 192.168.3.1     |

---

# Router Interface Addressing

## Router 1

| Interface | IP Address  | Network |
| --------- | ----------- | ------- |
| Gig0/0    | 192.168.1.1 | LAN 1   |
| Gig0/2    | 192.168.2.1 | LAN 2   |
| Gig0/1    | 10.10.0.1   | WAN     |

---

## Router 4

| Interface | IP Address  | Network |
| --------- | ----------- | ------- |
| Gig0/0    | 10.10.0.2   | WAN     |
| Gig0/1    | 192.168.3.1 | LAN 3   |

---

# Procedure

## Step 1: Place the Devices

Add the following devices to Cisco Packet Tracer:

* 2 Routers (2911 or 4331)
* 3 Switches (2960)
* 7 PCs

Arrange the devices into three separate LANs.

---

## Step 2: Connect the Devices

Use appropriate cables to connect the devices.

### LAN 1

```text
PC0 → Switch0
PC1 → Switch0
PC2 → Switch0
Switch0 → Router1 Gig0/0
```

### LAN 2

```text
PC3 → Switch1
PC4 → Switch1
Switch1 → Router1 Gig0/2
```

### LAN 3

```text
PC5 → Switch2
PC6 → Switch2
Switch2 → Router4 Gig0/1
```

### Router-to-Router Connection

```text
Router1 Gig0/1 → Router4 Gig0/0
```

Use the appropriate **Copper Cross-Over or Serial cable**, depending on the router/interface configuration.

---

## Step 3: Configure the PCs

Open:

```text
Desktop → IP Configuration
```

Assign the IP address, subnet mask, and default gateway according to the addressing tables.

For example, PC0:

```text
IP Address     : 192.168.1.2
Subnet Mask    : 255.255.255.0
Default Gateway: 192.168.1.1
```

Similarly, configure all seven PCs.

---

## Step 4: Configure Router 1

Open **Router 1 → CLI**.

Configure the interfaces according to the network plan.

### Configure GigabitEthernet0/0

```bash
Router1> enable
Router1# configure terminal

Router1(config)# interface gigabitEthernet 0/0
Router1(config-if)# ip address 192.168.1.1 255.255.255.0
Router1(config-if)# no shutdown
```

---

### Configure GigabitEthernet0/2

```bash
Router1(config)# interface gigabitEthernet 0/2
Router1(config-if)# ip address 192.168.2.1 255.255.255.0
Router1(config-if)# no shutdown
```

---

### Configure GigabitEthernet0/1

```bash
Router1(config)# interface gigabitEthernet 0/1
Router1(config-if)# ip address 10.10.0.1 255.255.255.0
Router1(config-if)# no shutdown
```

---

# Step 5: Configure Router 4

Open **Router 4 → CLI**.

### Configure GigabitEthernet0/0

```bash
Router4> enable
Router4# configure terminal

Router4(config)# interface gigabitEthernet 0/0
Router4(config-if)# ip address 10.10.0.2 255.255.255.0
Router4(config-if)# no shutdown
```

---

### Configure GigabitEthernet0/1

```bash
Router4(config)# interface gigabitEthernet 0/1
Router4(config-if)# ip address 192.168.3.1 255.255.255.0
Router4(config-if)# no shutdown
```

---

# Step 6: Configure Static Routes

This is the **core part of the experiment**.

Static routes tell the routers how to reach networks that are not directly connected to them.

---

## Static Route on Router 1

Router 1 needs to know how to reach **LAN 3 (192.168.3.0/24)**.

The next-hop address is Router 4's WAN IP:

```text
10.10.0.2
```

Configure:

```bash
Router1(config)# ip route 192.168.3.0 255.255.255.0 10.10.0.2
```

This means:

```text
To reach 192.168.3.0/24
        ↓
Forward packets to 10.10.0.2
        ↓
Router 4
```

---

## Static Routes on Router 4

Router 4 needs to know how to reach **LAN 1** and **LAN 2**.

The next-hop address is Router 1's WAN IP:

```text
10.10.0.1
```

### Route to LAN 1

```bash
Router4(config)# ip route 192.168.1.0 255.255.255.0 10.10.0.1
```

### Route to LAN 2

```bash
Router4(config)# ip route 192.168.2.0 255.255.255.0 10.10.0.1
```

---

# Step 7: Verify the Routing Table

Use the following command on both routers:

```bash
show ip route
```

Static routes should appear with the letter:

```text
S
```

For example:

```text
S    192.168.3.0/24 [1/0] via 10.10.0.2
```

The `S` indicates that the route was manually configured as a **Static Route**.

---

# Step 8: Test Connectivity

## Method 1: Ping Command

Open the Command Prompt on PC0:

```text
Desktop → Command Prompt
```

Run:

```bash
ping 192.168.3.3
```

Here:

```text
PC0 → Router 1 → Router 4 → PC6
```

If the configuration is correct, successful replies should be received.

---

## Method 2: Simple PDU

Use **Add Simple PDU** in Cisco Packet Tracer.

Send a packet from:

```text
PC0 → PC6
```

Where:

```text
PC0 = 192.168.1.2
PC6 = 192.168.3.3
```

The first attempt may fail because ARP needs to resolve the required MAC addresses.

After ARP resolution, the packet should be delivered successfully.

---

# Packet Flow

When PC0 communicates with PC6, the packet follows this path:

```text
PC0
192.168.1.2
   |
   ↓
Router 1
192.168.1.1
   |
   ↓
10.10.0.1
   |
   ↓
10.10.0.2
   |
   ↓
Router 4
192.168.3.1
   |
   ↓
PC6
192.168.3.3
```

The return packet follows the reverse path because Router 4 has a static route back to LAN 1.

---

# Commands Used

| Command         | Purpose                                      |
| --------------- | -------------------------------------------- |
| `ip address`    | Assigns an IP address to a router interface. |
| `no shutdown`   | Activates a router interface.                |
| `ip route`      | Creates a static route.                      |
| `show ip route` | Displays the routing table.                  |
| `ping`          | Tests network connectivity.                  |

---

# Understanding Static Routing

Static Routing means that the network administrator manually defines the path to a remote network.

For example:

```bash
ip route 192.168.3.0 255.255.255.0 10.10.0.2
```

The command can be understood as:

```text
Destination Network
        ↓
192.168.3.0/24

Next-Hop Router
        ↓
10.10.0.2
```

So Router 1 sends all traffic destined for **192.168.3.0/24** to Router 4 through **10.10.0.2**.

---

# Key Observations

* Different LANs require a router for communication between them.
* Each LAN must have a different network address.
* Every PC must have the correct **IP Address, Subnet Mask, and Default Gateway**.
* Router interfaces must be configured and activated using `no shutdown`.
* Static routes must be configured manually.
* Router 1 needs a route to LAN 3.
* Router 4 needs routes to LAN 1 and LAN 2.
* A **return path** is necessary for successful two-way communication.
* The first ping may fail because of the ARP process.
* The `show ip route` command can be used to verify static routes.

---

# Why Are Return Routes Important?

Suppose PC0 sends a packet to PC6:

```text
PC0 → Router 1 → Router 4 → PC6
```

PC6 will receive the packet successfully.

However, PC6 also needs to send a reply back to PC0:

```text
PC6 → Router 4 → Router 1 → PC0
```

Therefore, Router 4 must know how to reach:

```text
192.168.1.0/24
192.168.2.0/24
```

That's why we configured these static routes on Router 4:

```bash
ip route 192.168.1.0 255.255.255.0 10.10.0.1
ip route 192.168.2.0 255.255.255.0 10.10.0.1
```

Without these routes, communication may fail even if the forward path is correct.

---

# Static Routing vs Dynamic Routing

| Static Routing                                 | Dynamic Routing                     |
| ---------------------------------------------- | ----------------------------------- |
| Routes are manually configured.                | Routes are learned automatically.   |
| Suitable for small networks.                   | Suitable for larger networks.       |
| No routing protocol is required.               | Uses routing protocols.             |
| Requires manual updates when topology changes. | Can automatically adapt to changes. |
| Simple and predictable.                        | More flexible but more complex.     |

---

# Result

The two routers were successfully configured to connect three different LANs.

Static routes were manually added to provide paths between the remote networks. After configuring the correct IP addresses, default gateways, router interfaces, and static routes, successful communication was established between **PC0 (192.168.1.2)** and **PC6 (192.168.3.3)** using `ping` and **Simple PDU**.

---

# Conclusion

This lab demonstrated how **Static Routing** can be used to establish communication between multiple subnets through two routers.

We learned how to configure router interfaces, assign IP addresses to end devices, configure default gateways, and manually create static routes using the `ip route` command.

The experiment also showed that successful communication requires not only a forward path but also a proper **return path**. Therefore, static routing provides a simple and reliable solution for connecting small networks where the routes are known and do not change frequently.
