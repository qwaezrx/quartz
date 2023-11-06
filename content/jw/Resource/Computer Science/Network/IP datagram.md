
>A highly structured series of fields that are strictly defined

## IP datagram

![[IPv4_datagram_header.png]]

### Version
Indicates what version of Internet Protocol is being used.
- [[IPv4]] - most common
- [[IPv6]]

### IHL
Declares how long the entire header is.
- Almost always 20-bytes in length when dealing with [[IPv4]]
- 20-byte - minimum length of IP header

### Service type (TOS)
Specify details about quality of service, or [[QoS]], technologies

>[!important]
>There are services that allow [[Router]]s to make decisions about which IP datagram maybe more important than others

### Total length
Indicates the total length of the IP datagram it's attached to

### Identification
A 16-bit number that's used to group messages together

### Flag
Used to indicate if a datagram is allowed to be fragmented, or to indicate that the datagram has already been fragmented

>[!Fragmentation]
>The process of taking a single IP datagram and splitting it up into several smaller datagrams

### Time to live (TTL)
Indicates how many router hops a datagram can traverse before it's thrown away

### Protocol
Contains data about what transport layer protocol is being used

### Header checksum
A [[Checksum]] of the contents of the entire IP datagram header

### Source address (IP)

### Destination address (IP)

### Options
An optional field and is used to set special characteristics for datagrams primarily used for testing purposes

### Padding
A series of zeros used to ensure the header is the correct total size


