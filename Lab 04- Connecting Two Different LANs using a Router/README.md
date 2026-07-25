# Lab 04: Connecting Two Different LANs Using a Router (GUI Configuration)

## Overview

In this lab, we connected two different Local Area Networks (LANs) using a single router in Cisco Packet Tracer. Each LAN used a different IP network, and the router acted as the gateway to enable communication between them.

The router was configured using the **GUI (Config Tab)** instead of the CLI, making it easier to understand the basic routing process.

---

# Objectives

- Create two separate LANs using Hubs.
- Connect both LANs through a Router.
- Configure IP addresses and Default Gateways.
- Configure Router interfaces using the GUI method.
- Verify communication between different networks.

---

# Required Devices

| Device | Quantity |
|----------|---------:|
| Router (2911 / 4331) | 1 |
| Hub | 2 |
| PC | 5 |
| Copper Straight-Through Cable | As Required |

---

# Network Topology

```text
          LAN 1                           LAN 2

     PC0      PC1                    PC2     PC3     PC4
       \       |                       |       |       |
        \      |                       |       |       |
         +-----Hub0-----------------------------+
                 |                              |
                 | Gi0/0                 Gi0/1  |
                 +--------- Router ------------+
```

---

# Network Planning

Two different IP networks were used.

## LAN 1

| Network | 192.168.1.0/24 |
|----------|----------------|
| Gateway | 192.168.1.1 |

---

## LAN 2

| Network | 192.168.2.0/24 |
|----------|----------------|
| Gateway | 192.168.2.1 |

---

# IP Addressing Table

## LAN 1

| Device | IP Address | Subnet Mask | Default Gateway |
|---------|------------|-------------|-----------------|
| PC0 | 192.168.1.2 | 255.255.255.0 | 192.168.1.1 |
| PC1 | 192.168.1.3 | 255.255.255.0 | 192.168.1.1 |

---

## LAN 2

| Device | IP Address | Subnet Mask | Default Gateway |
|---------|------------|-------------|-----------------|
| PC2 | 192.168.2.2 | 255.255.255.0 | 192.168.2.1 |
| PC3 | 192.168.2.3 | 255.255.255.0 | 192.168.2.1 |
| PC4 | 192.168.2.4 | 255.255.255.0 | 192.168.2.1 |

---

# Procedure

## Step 1: Place the Devices

- Add one Router (2911 or 4331).
- Add two Hubs.
- Place two PCs on the left side.
- Place three PCs on the right side.

---

## Step 2: Connect the Devices

Use **Copper Straight-Through** cables.

Connections:

- PC0 → Hub0
- PC1 → Hub0
- Hub0 → Router GigabitEthernet0/0

- PC2 → Hub1
- PC3 → Hub1
- PC4 → Hub1
- Hub1 → Router GigabitEthernet0/1

Initially, the router interfaces remain **Red (Down)** because they are disabled.

---

## Step 3: Configure the PCs

Open:

```text
Desktop → IP Configuration
```

Assign the IP addresses according to the addressing table.

Configure the correct **Default Gateway** for every PC.

---

## Step 4: Configure the Router (GUI Method)

Open the Router.

Go to:

```text
Config Tab
```

### Configure GigabitEthernet0/0

Enable the interface by turning **Port Status** to **On**.

Assign:

```text
IP Address : 192.168.1.1
Subnet Mask : 255.255.255.0
```

---

### Configure GigabitEthernet0/1

Enable the interface.

Assign:

```text
IP Address : 192.168.2.1
Subnet Mask : 255.255.255.0
```

After enabling both interfaces, all router links become **Green**, indicating successful connections.

---

# Testing Connectivity

## Method 1: Simple PDU

Choose **Add Simple PDU**.

Send a packet from a PC in **LAN 1** to a PC in **LAN 2**.

Example:

```text
PC0  →  PC2
```

The first attempt may fail because the devices need to learn each other's MAC addresses through ARP.

The second attempt should display:

```text
Successful
```

---

## Method 2: Ping Command

Open the Command Prompt on **PC0**.

Execute:

```bash
ping 192.168.2.2
```

If replies are received successfully, communication between the two LANs has been established.

---

# Commands Used

| Command | Purpose |
|---------|---------|
| `ipconfig` | Displays the IP configuration of the PC. |
| `ping 192.168.2.2` | Tests connectivity between LAN 1 and LAN 2. |

---

# Key Observations

- Two different LANs cannot communicate without a Router.
- The Router acts as the Default Gateway for each network.
- Every PC must have the correct IP Address, Subnet Mask, and Default Gateway.
- Router interfaces remain inactive until the Port Status is turned **On**.
- Communication between different networks becomes successful after proper router configuration.
- The first ping may fail because ARP resolves the destination MAC address before communication begins.

---

# GUI Configuration vs CLI Configuration

| GUI Method | CLI Method |
|------------|------------|
| Uses the Config Tab. | Uses command-line interface. |
| Easy for beginners. | Preferred by network professionals. |
| No commands are required. | Requires configuration commands. |

---

# Result

The router successfully connected the two separate LANs. After assigning the correct IP addresses and enabling the router interfaces, devices from both networks communicated successfully using **Simple PDU** and the **ping** command.

---

# Conclusion

This lab demonstrated how a router connects multiple LANs and enables communication between different IP networks. By configuring router interfaces through the GUI and assigning proper IP settings, successful communication was established between all devices. The experiment also highlighted the importance of the Default Gateway in inter-network communication.