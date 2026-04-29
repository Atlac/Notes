 ### SFC
Service Function Chain (SFC) may be defined as the sequence of VNFs that a packet (or flow of packets) must traverse.

### SFC Architecture
SFC specify the path a packet should follow in the network also called SFP (Service Function Path).
The information about a packet belonging to a SPF are stored in an encapsulation header.

##### Service Plane functionalities
SFC aware network nodes can exploit the SFP to realize these functionalities. Packet forwarding in the underlying network is a task of the network protocol.

##### Service Function Path(SFP):
path that the packet should follow in the network

### Underlay and Overlay
**SFC** = overlay architecture built on top of an underlay architecture

**Underlay architecture** = ==provides connectivity== to the overlay network and is ==unaware== of the existence of the overlay

P2P links in the overlay are multi hop path in the underlay.
No specific technology to create the overlay architecture.


### Packet Tunneling
Encapsulation of a layer x PDU in a layer y PDU (with x ≥ y) is generally referred to as packet tunneling and is usedto connect two SFF and intermediate node will process only the outer header.
##### (PDU) Protocol data unit 
Represent the original data packet or payload.
Represent the original data packet (payload) encapsulated allowing to traverse foreign network.

##### Service Function Forwarder (SFF)
Key node in SFC directing traffic to specific services besed on NSH encapsualtion




### SFC Service Plane Logical Elements

- SFC Classifier:
	- classifies the incoming traffic based on predefined policies
	- add SFC header with the correct SFP identifier

- Service Functions(SF):
	- process packet along the chain
	- SFC aware or unaware

- Service Functions Forwarder (SFF):
	- Forward traffic to one or more connected Service Functions according to the information carried in the SFC header

- SFC Proxies:
	- remoce and insert SFC encapsulation on behalf of SFC-unaware SF


### Network Service Header (NSH)

- SPF indentification
- Transport independent chaining
- Packet basednetwork and metadata

Important Fields:
- Service Path Identifier(SPI): 24-bit  integer number assigned to packets by the first SFC Clasisfier in the SFP
- Service Index: 8-bit number that identify the position of the packet in the SFP, counter decreased each node.

Uses a look-up table for managing packet based on SPI/SI pairs