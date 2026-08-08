# 09. Connecting Multiple Subnets using Static Routing

> [!NOTE]
> **Static Routing** হলো এমন একটি routing method যেখানে Administrator manually Router-এর Routing Table-এ route configure করে দেয়।
>
> এই lab-এ **2টি Router এবং 3টি আলাদা LAN** ব্যবহার করে Static Routing-এর মাধ্যমে multiple subnet-এর মধ্যে communication establish করা হয়েছে।

---

# Table of Contents

* [Overview](#overview)
* [What is Routing?](#what-is-routing)
* [What is Static Routing?](#what-is-static-routing)
* [Network Topology](#network-topology)
* [IP Planning](#ip-planning)
* [IP Addressing Table](#ip-addressing-table)
* [Physical Setup](#physical-setup)
* [Cabling](#cabling)
* [PC Configuration](#pc-configuration)
* [Router Interface Configuration](#router-interface-configuration)
* [What is a Static Route?](#what-is-a-static-route)
* [Static Route Configuration](#static-route-configuration)
* [How Static Routing Works](#how-static-routing-works)
* [Verify Routing Table](#verify-routing-table)
* [Testing Connectivity](#testing-connectivity)
* [Communication Flow](#communication-flow)
* [Advantages](#advantages)
* [Disadvantages](#disadvantages)
* [Common Errors](#common-errors)
* [Troubleshooting Checklist](#troubleshooting-checklist)
* [Quick Reference](#quick-reference)
* [Viva Questions](#viva-questions)
* [Quick Revision](#quick-revision)
* [Exam Tips](#exam-tips)

---

# Overview

এই lab-এ **দুইটি Router** ব্যবহার করে **তিনটি আলাদা LAN/Subnet** connect করা হয়েছে।

Topology-তে:

* Router 1-এর সাথে LAN 1 এবং LAN 2 connected।
* Router 4-এর সাথে LAN 3 connected।
* Router 1 এবং Router 4 একটি WAN link-এর মাধ্যমে connected।
* দুই Router-এর মধ্যে **Static Route** configure করা হয়েছে।
* এরপর এক LAN থেকে অন্য LAN-এ `ping` এবং **Simple PDU** ব্যবহার করে connectivity test করা হয়েছে।

---