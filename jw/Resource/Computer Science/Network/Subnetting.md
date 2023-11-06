
>The process of taking a large network and splitting it up into many individual and smaller subnetworks, or [[Subnet]]s

>[!note]
>Incorrect subnetting setups are a common problem you might run into as an IT support specialist.

[[Address class]] give us a way to break the total global [[IP]] space into discrete networks.

If you want to communicate with the IP address 9.100.100.100: 
1. core [[Router]]s on the [[Internet]] know that this IP belongs to the 9.0.0.0 Class A network.
2. Then they route the message to the [[Gateway router]] responsible for the network by looking at the [[Network ID]].
3. A [[Gateway router]] specifically serves as the entry and exit path to a certain network.
	- You can contrast this with core Internet routers which might only speak to other [[Core router]]s
4. Once your packet gets to the gateway router for the 9.0.0.0 Class A network, that router is now responsible for getting that data to the proper system by looking at the [[Host ID]].
5. With [[Subnet]]s, split your large network up into many smaller ones. These individual subnets will all have their own [[Gateway router]]s serving as the ingress and egress point for each subnet.