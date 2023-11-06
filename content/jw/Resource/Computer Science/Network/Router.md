---
tags:
  - CS/Network
---

![[icons8-router-50.png]]

>A device that knows how to forward data between independent networks

## Introduction
When we want to send or receive data to computers on other networks, This is when outers come into play.

To determine "where" to send things:
- [[Switch]]s   -Inspect->   [[Ethernet]]
- Routers   -Inspect->   [[IP]]

__Routers__ store internal tables containing information about how to route traffic between lots of different networks all over the world.

The most common type of router you'll see is one for home network or a small office. These devices generally don't have very detailed routing tables. The purpose of these routers is just to take traffic originating from inside the home or office and to forward it along to the [[ISP]].

Once traffic is at the ISP, way more sophisticated type of router takes over. These core routers form the backbone of the [[Internet]] and directly responsible for how we send and receive data all over the internet every day.

The Core [[ISP]] routers usually has many different connections to many other routers. Routers share data with each other via protocol known as [[BGP]] (Border Gateway Protocol). 

## Summary
The Internet is incredibly large and complicated, and routers are global guides for getting traffic to the right places.


## Additional Resources

Previous: [[Switch]]

Next: [[Servers & Clients]]