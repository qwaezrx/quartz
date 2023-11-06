
>The layer in which the first protocols are introduced. 
>This layer is responsible for defining a common way of interpreting signals, so network devices can communicate.

## Introduction
The 2nd layer of TCP/IP model

## Purpose
One of the primary purpose of this layer is to essentially abstract away the need for any other layers to care about the [[Physical layer]] and what [[Hardware]] is in use.

By dumping this responsibility on the data link layer, the [[Transport layer]] and [[Application layer]]s can all operate the same no matter how the device they're running on is connected.

For example, your web browser doesn't need to know if it's running on a device connected via [[Twisted pair]] or wireless connection. It just needs the underlying layers to send and receive data for it.

## Related Documents
- [[Ethernet]]
- [[MAC]]