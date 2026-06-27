# Lab 01: Introduction to Cisco Packet Tracer and Basic Network Connectivity

## Overview

This lab introduces the basic features of **Cisco Packet Tracer** and demonstrates how to create a simple **Peer-to-Peer network** using two computers.

The main goal of this lab is to learn how to:

* Connect two PCs using a Copper Cross-over cable.
* Configure IP addresses manually.
* Test network connectivity using the `ping` command.
* Understand the difference between Realtime Mode and Simulation Mode.

---

# Objectives

* Become familiar with the Cisco Packet Tracer interface.
* Create a basic Peer-to-Peer network.
* Configure Class A IP addresses.
* Verify communication between two computers.
* Learn basic networking commands.

---

# Required Tools

| Tool                    | Description                 |
| ----------------------- | --------------------------- |
| Cisco Packet Tracer     | Network simulation software |
| Generic PC              | 2                           |
| Copper Cross-over Cable | 1                           |

---

# Network Topology

```text
PC0 -------------------- PC1
```

* Topology Type: **Peer-to-Peer**
* Connection Type: **Copper Cross-over Cable**
* Interface: **FastEthernet0**

---

# IP Configuration (Class A)

| Device | IP Address | Subnet Mask | IP Class |
| ------ | ---------- | ----------- | -------- |
| PC0    | 10.0.0.1   | 255.0.0.0   | Class A  |
| PC1    | 10.0.0.2   | 255.0.0.0   | Class A  |

---

# Procedure

## Step 1: Create the Topology

* Open Cisco Packet Tracer.
* Add two Generic PCs to the workspace.
* Connect them using a **Copper Cross-over Cable**.
* Connect **FastEthernet0** of PC0 to **FastEthernet0** of PC1.

---

## Step 2: Configure IP Addresses

Open:

```text
Desktop → IP Configuration
```

Assign the following addresses:

| Device | IP Address |
| ------ | ---------- |
| PC0    | 10.0.0.1   |
| PC1    | 10.0.0.2   |

Subnet Mask:

```text
255.0.0.0
```

---

## Step 3: Verify the IP Configuration

Open **Command Prompt** on PC0.

Run:

```bash
ipconfig
```

This command displays the current IP address, subnet mask, and network configuration.

---

## Step 4: Test Network Connectivity

From **PC0**, execute:

```bash
ping 10.0.0.2
```

From **PC1**, execute:

```bash
ping 10.0.0.1
```

If the configuration is correct, both devices will receive **four successful replies** with **0% packet loss**.

---

## Step 5: Observe Packet Flow

Switch to **Simulation Mode**.

Use the **Capture/Forward** button to observe how packets move between the two computers.

You can also return to **Realtime Mode** for normal network operation.

---

# Commands Used

| Command             | Purpose                                                        |
| ------------------- | -------------------------------------------------------------- |
| `ipconfig`          | Displays the IP address and subnet mask of the local computer. |
| `ping <IP Address>` | Tests connectivity between two network devices.                |

---

# What Happens During Ping?

1. PC0 sends an ICMP Echo Request to PC1.
2. PC1 receives the request.
3. PC1 sends an ICMP Echo Reply back to PC0.
4. The ping command confirms successful communication.

---

# Realtime Mode vs Simulation Mode

| Realtime Mode                      | Simulation Mode                         |
| ---------------------------------- | --------------------------------------- |
| Network operates normally.         | Displays packet movement step by step.  |
| Packets are transmitted instantly. | Useful for observing protocol behavior. |
| Best for testing connectivity.     | Best for learning packet flow.          |

---

# Key Observations

* A **Copper Cross-over Cable** is required to connect two similar devices directly.
* Both devices must belong to the same network.
* Correct IP configuration is necessary for successful communication.
* The `ping` command verifies whether two devices can communicate.
* Simulation Mode helps visualize packet transmission.

---

# Result

The two computers communicated successfully after assigning the correct IP addresses. The ping test returned successful replies with **0% packet loss**, confirming that the network was configured correctly.

---

# Conclusion

This lab provided a basic understanding of Cisco Packet Tracer and Peer-to-Peer networking. We learned how to connect two computers, configure IP addresses, and verify communication using the `ping` command. The experiment also introduced Simulation Mode for observing packet flow and basic network operations.
