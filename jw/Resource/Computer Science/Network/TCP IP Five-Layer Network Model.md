---
tags:
  - CS/Network
---


| #   | Layer Name  | Protocol           | Protocol Data Unit | Addressing  |
| --- | ----------- | ------------------ | ------------------ | ----------- |
| 5   | [[Application layer]] | [[HTTP]], SMTP, etc... | Messages           | N/A         |
| 4   | [[Transport layer]]   | [[TCP]]/[[UDP]]            | [[Segment]]            | Port #'s    |
| 3   | [[Network layer]]     | [[IP]]                 | [[Packet]] / Datagram  | IP Address  |
| 2   | [[Data link layer]]   | [[Ethernet]], [[Wi-Fi]]    | [[Frame]]s             | MAC Address |
| 1   | [[Physical layer]]    | N/A                | Bits               | N/A         |

---

## 1.  Physical layer

> Represents the physical devices that interconnect computers

This includes the specifications for the networking [[Cable]]s and the connectors that join devices together along with specifications describing how signals are sent over their connections.

---

## 2. Data link layer

> Responsible for defining a common way of interpreting these signals so network devices can communicate across a single link

>[!Ethernet]
>The [[Ethernet]] standards also define a protocol responsible for getting data to nodes on the same network or link.

---

## 3. Network layer

>Allows different networks to communicate with each other through devices known as __[[Router]]__.

The [[Network layer]] delivers data between two individual nodes.

>[!Internetwork]
>A collection of networks connected together through __routers__, the most famous of these being the __internet__.

While the data link layer is responsible for getting data across a single link, the network layer is responsible for getting data delivered across a __collection of networks__.

>[!IP]
>The heart of the Internet and most smaller networks around the world

Network software is usually divided into [[Client]] and [[Server]] categories with the client application initiating a request for data and the server software answering the request across the network. 

A single node may be running multiple client or server applications.

---

## 4. Transport layer

>Sorts out which client and server programs are supposed to get that data

While the network layer delivers data between two individual nodes, the transport layer sorts out which client and server programs are supposed to get that data.

>[!TCP & UDP]
>__Transmission control protocol ([[TCP]])__ provides mechanisms to ensure that data is reliably delivered while __User datagram protocol ([[UDP]])__ does not

---

## 5. Application layer

There are lots of different protocols at this layer and they are application specific. Protocols used to allow you to browse the web or send and receive email are some common ones.

---

## Summary
- __[[Physical layer]]__ : Delivery truck and the roads
- __[[Data link layer]]__ : How the delivery trucks get from one intersection to the next over and over
- __[[Network layer]]__ : Identifies which roads need to be taken to get from A to B
- __[[Transport layer]]__ : Ensures that delivery driver knows how to know on your door to tell you your package has arrived
- __[[Application layer]]__ : Contents of the package itself
 
![[Screenshot 2023-08-19 at 8.20.44 PM.png]]

> [!important]
> Each layer is needed for one above it

---

## Supplementary reading for the [[OSI model]]

In addition to the five layer model we are working with, it’s important to note that other models exist. The traditional TCP/IP Model only has four layers, as it doesn’t differentiate between the physical layer and the data link layer, but is otherwise very similar to the one we’ll be working with. 

The most well known other model is the __OSI model__. It’s the model taught by many other networking certificate programs, like Net+ and Cisco’s many networking certifications. The primary difference between our five layer model and the seven layer OSI model is that the OSI model abstracts the application layer into three layers total.
