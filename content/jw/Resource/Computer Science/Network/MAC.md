## MAC address

>A __globally unique__ identifier attached to an individual network interface.
>48-bit number normally represented by six groupings of two [[Hexadecimal]] numbers.

## Sections
### 1. Organizationally Unique Identifier (OUI)

>The first three octets of a MAC address

These are assigned to individual hardware manufacturers by the [[IEEE]].
It means that you can always identify the manufacturer by MAC address.
### 2. Vendor Assigned
- Can be assigned any way the manufacturer would like.

|                  | Organizational Unique Identifier | Vendor Assigned (NIC Cards, Interfaces) |
| ----------------- | -------------------------------- | --------------------------------------- |
| Size (bits)       | 24                               | 24                                      |
| Size (hex digits) | 6 Hex Digits                     | 6 Hex Digits                            |
| Example           | 00 A0 EF                         | A1 9B CC                                |
| Structure         | Cisco                            | Particular Device                       |

## Ethernet

[[Ethernet]] uses MAC addresses to ensure that the data it sends has both an address for:
- machine that sent the transmission
- one the transmission was intended for

## Limitations
- Every single [[Network interface]] on the planet has a unique MAC address, and they are not ordered in any systematic way.
- There's no way of knowing where on the planet a certain MAC address might be at any one point in time.
- So it is not ideal for communicating across distances.