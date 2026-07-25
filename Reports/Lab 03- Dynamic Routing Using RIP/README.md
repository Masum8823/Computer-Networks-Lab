# Lab 03: Dynamic Routing Using RIP (Routing Information Protocol)

## Overview

In this lab, we configured **RIP Version 2 (Routing Information Protocol)** to establish communication between multiple Local Area Networks (LANs). The experiment demonstrates how routers exchange routing information automatically and how RIP selects the shortest path using **Hop Count**.

Communication was tested between **PC4 (Sender)** and the **Server (Receiver)** located in different LANs.

---

# Objectives

- Configure RIP Version 2 on multiple routers.
- Connect different LANs using dynamic routing.
- Understand the concept of Hop Count.
- Observe how RIP selects the shortest available path.
- Verify communication using `ping` and `tracert`.
- Display dynamically learned routes using the router CLI.

---

# Required Devices

| Device | Quantity |
|---------|---------:|
| Router | 4 |
| Switch | 4 |
| PCs | 7 |
| Server | 1 |
| Copper Straight-Through Cable | As Required |
| Serial DCE Cable | As Required |

---

# Network Topology

```
                    Router4
                  /         \
             Router5       Router6
                |             |
             LAN 1          LAN 2
                \
                 \
                Router7
                   |
                 LAN 3
```

**Sender:** PC4 (LAN 3)

**Receiver:** Server (LAN 1)

---

# IP Configuration

## End Devices

| Device | IP Address | Default Gateway |
|---------|------------|-----------------|
| PC4 | 192.168.3.10 | 192.168.3.1 |
| Server | 192.168.1.10 | 192.168.1.1 |

> Other devices were configured according to their respective LANs.

---

# Router Networks

Example router networks:

| Network |
|----------|
| 10.0.0.0 |
| 11.0.0.0 |
| 12.0.0.0 |

---

# Procedure

## Step 1

Create the network topology in Cisco Packet Tracer.

- Connect all PCs and the Server to their respective switches.
- Connect routers using Serial DCE cables.
- Connect each router to its corresponding LAN.

---

## Step 2

Assign static IP addresses to all end devices.

Configure the correct Default Gateway for each LAN.

---

## Step 3

Configure router interfaces.

Assign IP addresses and activate every interface.

```text
no shutdown
```

---

## Step 4

Configure RIP Version 2.

Example:

```text
Router(config)# router rip
Router(config-router)# version 2
Router(config-router)# network 10.0.0.0
Router(config-router)# network 11.0.0.0
Router(config-router)# network 12.0.0.0
Router(config-router)# no auto-summary
```

Configure all routers using their directly connected networks.

---

## Step 5

Verify communication from **PC4**.

```bash
ping 192.168.1.10
```

The ping reply confirms successful communication.

---

## Step 6

Check the packet path.

```bash
tracert 192.168.1.10
```

Observed path:

```
PC4
 ↓
Router7
 ↓
Router4
 ↓
Router5
 ↓
Server
```

The longer path through **Router6** was not selected.

---

## Step 7

Display the RIP routing table.

```text
show ip route rip
```

This command displays all routes learned dynamically through RIP.

---

# Commands Used

| Command | Purpose |
|---------|---------|
| `router rip` | Starts RIP configuration mode |
| `version 2` | Enables RIP Version 2 |
| `network <network-id>` | Advertises connected networks |
| `no auto-summary` | Disables automatic summarization |
| `no shutdown` | Activates router interfaces |
| `show ip route rip` | Displays RIP learned routes |
| `ping 192.168.1.10` | Tests end-to-end connectivity |
| `tracert 192.168.1.10` | Displays the routing path |

---

# How RIP Works

1. Routers exchange routing information.
2. Each router updates its routing table.
3. RIP calculates the Hop Count for every available route.
4. The route with the lowest Hop Count is selected.
5. Packets are forwarded through the shortest available path.

---

# Hop Count Analysis

Two routes were available.

## Path A

```
PC4
 ↓
Router7
 ↓
Router4
 ↓
Router5
 ↓
Server
```

**Hop Count = 2**

---

## Path B

```
PC4
 ↓
Router7
 ↓
Router4
 ↓
Router6
 ↓
Router5
 ↓
Server
```

**Hop Count = 3**

Since RIP always chooses the route with the **lowest Hop Count**, **Path A** was selected.

---

# RIP Features

- Dynamic Routing Protocol
- Distance Vector Algorithm
- Uses Hop Count as the routing metric
- Maximum Hop Count = 15
- Supports Classless Routing (Version 2)
- Automatically exchanges routing information

---

# Key Observations

- Communication between different LANs was successful.
- RIP dynamically updated the routing table.
- The shortest route was selected automatically.
- `tracert` displayed every router on the selected path.
- `show ip route rip` confirmed that routing information was learned successfully.
- RIP ignored the longer path because it had a higher Hop Count.

---

# Result

After configuring RIP Version 2, all routers exchanged routing information successfully. PC4 communicated with the Server without requiring static routes. The `tracert` command confirmed that packets followed the shortest available path based on Hop Count.

---

# Conclusion

This lab demonstrated the practical implementation of **RIP Version 2** in a multi-router network. We learned how routers exchange routing information automatically and how RIP selects the shortest path using Hop Count. By using **ping**, **tracert**, and **show ip route rip**, we successfully verified both connectivity and routing behavior across multiple LANs.