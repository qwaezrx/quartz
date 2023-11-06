
> [[Data packet]] at the [[Ethernet]] level which is a highly structured collection of information presented in a specific order

Almost all sections of an Ethernet frame are mandatory, and most of them have a fixed size.


| Section             | Size (byte) | Description                                                                                                                         |
| ------------------- | ----------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Preamble            | 7           | Itself be split into two sections, first 7 bytes are a series of alternating 1s & 0s. Which act partially as a buffer between frames. Also can be used by network interfaces to synchronize internal clocks they use to regulate the speed at which they send data.                                                                                                   |
| SFD                 | 1           | Start frame delimiter<br>Signals to a receiving device that the preamble is over and that the actual frame contents will now follow |
| Destination [[MAC]] address | 6           | The hardware address of the intended recipient.                                                                                                                                    |
| Source address      | 6           | Where the frame originated from.                                                                                                                                    |
| [[VLAN]] header         | 4           | Indicates that the frame itself is what's called a VLAN frame.<br>If a VLAN header is present, the EtherType field follows it. Any frame with a VLAN tag will only be delivered out of a [[Switch]] interface configured to relay that specific tag.                                                                                                                                    |
| Ether-type          | 2           | Used to describe the protocol of the contents of the frame.                                                                                                                                    |
| [[Payload]]             | 46 - 1500   | Contains all of the data from the higher layers.                                                                                                                                   |
| FCS                 | 4           | Frame check sequence<br>Represents a checksum value for the entire frame. Which is done by [[CRC]].                                                                                                                                    |


When a device gets ready to send an Ethernet frame:
1. it collects all the information above. 
2. Then it performs a [[CRC]] against that data 
3. attaches the resulting [[Checksum]] number as the frame check sequence at the end of the frame. 
4. Then data is then sent across a link and received at the other end.
5. All various fields of the Ethernet frame are collected
6. Receiving side performs [[CRC]] against that data.
7. if the [[Checksum]] computed by the receiving end doesn't match the checksum in the frame -> data is thrown out.

>[!important]
>Ethernet itself only perform data integrity, it doesn't perform data recovery

