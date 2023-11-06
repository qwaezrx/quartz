

__Types of [[Ethernet]] transmissions__

| Least significant bit in the first [[Octet]] of a destination address | Meaning                                                          |
| ---------------------------------------- | ---------------------------------------------------------------- |
| 0                                        | Ethernet frame is intended for __only the destination address__. [[Unicast]] |
| 1                                        | Dealing with [[Multicast]] frame.                                                                 |

## Unicast
A unicast transmission is always meant for just one receiving address.
At the [[Ethernet]] level this is done by looking at a special bit in the destination [[MAC]] address.

If the __least significant bit([[LSB]]) in the first [[Octet]] of a destination address__ is set to __0__, means it that ethernet frame is intended for only the destination address.

## Multicast
If the __[[LSB]] in the first [[Octet]]__ is set to __1__.

Multicast frame is similarly set to all devices on the local network [[Segment]].
What's different is that it will be accepted or discarded by each device depending on criteria aside from their own hardware [[MAC]] address.

[[Network interface]]s can be configured to accept list of configured multicast addresses for these sorts of communications.

## Broadcast
In [[Ethernet]], broadcast is sent to every single device on [[LAN]]. This is accomplished by using a special destination known as a broadcast address. 

The ethernet broadcast address is all F's.
