# Lab 02: ARP and ICMP Analysis Using Hub and Switch

## Overview

In this lab, we created a Local Area Network (LAN) using a **Cisco 2960 Switch**, a **Generic Hub**, several **PCs**, and a **Server** in Cisco Packet Tracer.

The main purpose of this lab was to understand:

* How **ARP (Address Resolution Protocol)** works.
* How **ICMP (Internet Control Message Protocol)** works.
* The difference between **Hub** and **Switch**.
* How a Switch learns MAC addresses.
* How to verify communication using the `ping` command.

---

# Objectives

* Understand the working principle of Hub and Switch.
* Analyze the behavior of ARP and ICMP protocols.
* Observe broadcasting and unicasting.
* Learn how a Switch builds its MAC Address Table.
* Verify network connectivity using CLI commands.

---

# Network Topology

```
                Switch
      ┌────┬────┬────┬────┬────┐
     PC1  PC2  PC3  PC4 Server
        │
       Hub
    ┌───┼───┐
   PC5 PC6 PC7
```

### Device Summary

| Device            | Quantity |
| ----------------- | -------: |
| Cisco 2960 Switch |        1 |
| Generic Hub       |        1 |
| PCs               |        7 |
| Server            |        1 |

---

# IP Configuration (Class A)

| Device | IP Address | Subnet Mask |
| ------ | ---------- | ----------- |
| PC1    | 10.0.0.1   | 255.0.0.0   |
| PC2    | 10.0.0.2   | 255.0.0.0   |
| PC3    | 10.0.0.3   | 255.0.0.0   |
| PC4    | 10.0.0.4   | 255.0.0.0   |
| Server | 10.0.0.5   | 255.0.0.0   |
| PC5    | 10.0.0.6   | 255.0.0.0   |
| PC6    | 10.0.0.7   | 255.0.0.0   |
| PC7    | 10.0.0.8   | 255.0.0.0   |

---

# Procedure

## Step 1

Create the topology in Cisco Packet Tracer.

* Add one Cisco 2960 Switch.
* Add one Generic Hub.
* Add seven PCs and one Server.
* Connect all devices using Copper Straight-Through cables.

---

## Step 2

Assign IP addresses to every device.

Example:

```
PC5 : 10.0.0.6
PC1 : 10.0.0.1
Server : 10.0.0.5
Subnet Mask : 255.0.0.0
```

---

## Step 3

Switch to **Simulation Mode**.

Enable only:

* ARP
* ICMP

This helps observe only the required packets.

---

## Step 4

Open the **Command Prompt** of **PC5**.

Ping another PC connected to the Switch.

```bash
ping 10.0.0.1
```

---

## Step 5

Repeat the test by pinging the Server.

```bash
ping 10.0.0.5
```

---

## Step 6

Open the Switch CLI.

Run the following commands.

```text
Switch> enable
Switch# show mac address-table
```

The Switch displays all learned MAC addresses and their corresponding ports.

---

# Commands Used

| Command                  | Purpose                                       |
| ------------------------ | --------------------------------------------- |
| `ipconfig`               | Shows IP configuration of the local device.   |
| `ping <IP>`              | Tests connectivity between two devices.       |
| `enable`                 | Enters Privileged EXEC mode on the Switch.    |
| `show mac address-table` | Displays the MAC Address Table of the Switch. |

---

# ARP Workflow

When the ping command is executed for the first time:

1. The source device does not know the destination MAC address.
2. It sends an **ARP Request**.
3. The Hub broadcasts the ARP packet to every connected device.
4. The Switch forwards the request toward the destination.
5. Devices with different IP addresses ignore the request (shown as **Red X** in Simulation Mode).
6. The destination replies with an **ARP Reply** containing its MAC address.
7. The source stores the MAC address in its ARP Cache.

---

# ICMP Workflow

After ARP completes:

1. The source sends an **ICMP Echo Request**.
2. The destination receives the packet.
3. The destination sends an **ICMP Echo Reply**.
4. The ping command becomes successful.

---

# Hub vs Switch

| Hub                              | Switch                                      |
| -------------------------------- | ------------------------------------------- |
| Broadcasts packets to all ports. | Sends packets only to the destination port. |
| Does not learn MAC addresses.    | Learns and stores MAC addresses.            |
| More unnecessary traffic.        | Less network traffic.                       |
| Slower performance.              | Better performance.                         |

---

# ARP vs ICMP

| ARP                                | ICMP                              |
| ---------------------------------- | --------------------------------- |
| Finds the destination MAC address. | Tests network connectivity.       |
| Works before communication starts. | Works after ARP completes.        |
| Uses ARP Request and Reply.        | Uses Echo Request and Echo Reply. |

---

# MAC Address Table

The Switch automatically learns MAC addresses from incoming frames.

Use the following command to verify:

```text
show mac address-table
```

Benefits:

* Faster forwarding
* Less broadcasting
* Better network performance

---

# Key Observations

* The Hub broadcasts ARP packets to every connected device.
* The Switch forwards packets intelligently after learning MAC addresses.
* ARP always runs before ICMP.
* ICMP verifies connectivity using the ping command.
* Devices with unmatched IP addresses reject the ARP request and show a **Red X**.
* The communication process remains the same whether the destination is a **PC** or a **Server**.

---

# Conclusion

This lab demonstrated how ARP and ICMP work together in a Local Area Network.

We observed that ARP first resolves the destination MAC address, after which ICMP verifies connectivity. We also learned the functional difference between a Hub and a Switch and examined the Switch's MAC Address Table using CLI commands.

Overall, the lab provided a practical understanding of packet transmission, MAC learning, broadcasting, and unicasting in Cisco Packet Tracer.
