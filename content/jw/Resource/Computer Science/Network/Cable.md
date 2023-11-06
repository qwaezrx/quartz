## Introduction
Lots of different cables and network devices can be used to allow computers to communicate with each other.

>[!Cables]
>Connect different devices to each other, allowing data to be transmitted over them

Most network cables used today can be split into two categories:
- [[Copper cables]]
- [[Fiber optic cables]]

---

## Twisted pair cable

>The most common type of cabling for connecting computing devices.
>It features pairs of copper wires that are twisted together.

These pairs act as a single conduit for information and their twisted nature helps protect against electromagnetic interface and cross-talk from neighboring pairs.

A standard __Cat6__ cable has 8 wires consisting of 4 twisted pairs inside a single jacket. Exactly how many pairs are actually in use depends on the transmission technology being used.

---

## Duplex communication vs. Simplex communication

| Duplex communication                                                      | Simplex communication          |
| ------------------------------------------------------------------------- | ------------------------------ |
| The concept that information<br> can flow in both directions <br>across the cable | This process is unidirectional |
 
>[!Important]
>In modern forms of networking, these cables allow for duplex communication

The way networking cables ensure that duplex communication is possible is by reserving one or two pairs fro communicating in one direction. They then use the other one or two pairs for communicating in the other direction.

>[!Full duplex]
> Devices on either side of a networking link can both communicate with each other at the exact same time. This is known as full-duplex.

If there's something wrong with the connection, you might see a network link to grade and report itself as half-duplex.

>[!Half duplex]
>Means that while communication is possible in each direction, only one device can be communicating at a time.

## Related Documents

- Next: [[Switch]]
- [[Physical layer]]
- [[Twisted pair Ethernet]]
