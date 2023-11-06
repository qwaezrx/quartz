---
tags:
  - CS/Network
---

## Introduction
__[[Twisted pair]] [[Ethernet]] cable__ is the most commonly used [[Ethernet]] cable in business and home networks. An internet connection to a building or home is normally delivered through a __[[Coaxial cable]]__ and/or [[Fiber optic]] cable from an internet service provider ([[ISP]]). This connection is fed into a gateway modem located inside the building or home. 

The modem then passes the internet connection through a __twisted pair Ethernet cable__ to a router or a single computer. The router uses __twisted pair Ethernet cables__ to distribute wired network connections internally to the business or home.

These network cables are also called __CAT__ cables. It is possible that you have purchased an Ethernet CAT5 or CAT6 cable for your home internet connection.

Some [[Router]]s also have the capability to provide wireless network connections to the internet network.

In addition, [[Ethernet]] over twisted pair technologies can also supply telephone and television services to business and homes.

---

## Twisted pair cables

Originally, telephone and early data cables included two copper wires, one for transmitting data and one for receiving data. The two wires laid parallel to one another. This configuration was affected by electromagnetic interference [[EMI]], radio frequency interference [[RFI]], and [[Crosstalk]] between the two copper wires. One of the initial engineering steps to resolve these issues involved twisting the wire pair together, which reduced some of the extra noise on the lines.

Twisted pair Ethernet cables are commonly used in [[LAN]]s because:
- They offer multiple levels of protection against [[EMI]], [[RFI]], and [[Crosstalk]].
- The lower levels of interference protection provide low-cost options, which are generally more accessible to home users and small businesses.
- The cables are thin, light weight, and malleable enough to install and move easily.
- The transmission range of the cable is suitable for short distance connections inside of building and homes.
- The cable's frequency range is able to transmit both data and telephone/voice communications.

### UTP, STP, and FTP Ethernet cables
Twisted pair Ethernet cables uses four pairs of color-coded copper wires. Each colored pair, one solid and one striped, are twisted together. There are multiple types of twisted pair Ethernet cables available on the market.

These types fall into three main categories:
- __Unshielded twisted pair__ [[UTP]] 
	- The most common and least expensive type of Ethernet cable found in business and home networks. UTP cables offer very basic protection against EMI, RFI, and crosstalk interference.
- __Shielded twisted pair__ [[STP]]
	- Used in environments where EMI, RFI, and crosstalk with nearby cables have been identified as a problem for network communications.
	- Uses braided aluminum and/or copper shielding to encase the four twisted pairs underneath the outer jacket.
- __Foiled twisted pair__ [[FTP(network)]]
	- Also used in environments with EMI, RFI, and crosstalk problems.
	- Uses a thin foil shield that wraps around the bundle of twisted pair wires underneath the outer jacket.

---

## Straight-through cable

Aka. patch cables, are the primary type of Ethernet cable used in computer networks. Straight-through cables normally connect:
- computers and routers --> hubs and Ethernet switches
Ethernet cable can also connect:
- servers --> Ethernet switches.

Straight-through cable can be identified by comparing both ends of the cable with one another. The cable is a straight-through cable if the color and stripe order of the twisted pairs are in the same position on both ends of the cable. 

In a typical straight-through cable set-up, an orange-striped wire that appears in pin position 1 should also appear at that some position on the other end. This one-to-one pattern is continued for each color in pin positions 2-8.

Ethernet cables that use [[100Base-T standards]] (common for home networks) do not use blue and brown cables. [[Networks]] using gigabit Ethernet have the option to use blue and brown cables for Power over Ethernet ([[PoE]]).
### Straight-through cable key:
- [[Computer]]s and [[Router]]s use:
	- Pins 1 & 2 - Orange wires for sending data
	- Pins 3 & 6 - Green wires for receiving data
- [[Hub]]s and [[Switch]]es use:
	- Pins 1 & 2 - Green wires for sending data
	- Pins 3 & 6 - Orange wires for receiving data

---

## Crossover cables

Crossover cables may still be in use in older network environments.

>[!Note]
>Most new Enterprise devices have the ability to detect Ethernet connection types and select the correct wires for sending and receiving data using Auto Medium Dependent Interface Crossover Auto-MDI/MDIX technology.

The Auto-MDI/MDIX ports replace the crossover cable's function for connecting two devices that use the same sending and receiving wires for data communications.

<u>Crossover cables are used to connect two computing devices directly to one another.</u>
A crossover cable should be connected between the Ethernet port/Network Interface Card ([[NIC]]) on the IT administrative system and the management [[Port (networking)]] of the Enterprise machine. This connection is then used to access the [[OS]] and/or the management interface of the Enterprise machine. Additionally, crossover cables can connect two [[Switch]]s, two [[Hub]]s, or a switch to hub, as well as two [[Router]]s, two [[PC]]s, or a router to PC.

Like [[Straight-through cable]]s, crossover cables can also be identified by comparing both ends of the cable to one another. Crossover cables will have different patterns in the color order of the twisted pairs. The crossover cable key below describes a typical setup for a T-568-A. If the green wires appear in pin positions 1 and 2 on one side of the cable, on the opposite end of the cable, the green wires will appear in the pin positions 3 and 6. The orange wires will appear in positions 3 and 6 at one end of the cable, crossing over to the 1 and 2 positions at the opposite end.

For the T-568-B scheme, if you see orange wires start at pin positions 3 and 6, they should cross over to pin positions 1 and 2 at the opposite end of the cable. Green wires should start at pin positions 1 and 2, crossing over to 3 and 6 at the opposite end. This wiring crossover is needed to connect two computers that transmit and receive data on the same wires. Blue and brown wires do not cross over to different positions in this set-up.

Straight-through cables use the T568B wiring scheme, while crossover cables use both schemes.

**Crossover cable key:**
- Endpoint 1 of the Ethernet cable:
	- Pins 1 & 2 - Green wires for sending data
	- Pins 3 & 6 - Orange wires for receiving data 
	    
- Endpoint 2 of the Ethernet cable:
    - Pins 1 & 2 - Orange wires for sending data
    - Pins 3 & 6 - Green wires for receiving data

---

## Additional Resources

- - [Why are Wires Twisted in Twisted Pair Cables?](https://www.systoncable.com/why-are-wires-twisted-in-twisted-pair-cables/) - Explains the physics of how twisting the wires in twisted pair Ethernet cables reduces interference on the wires.