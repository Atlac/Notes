Leverages Source destination routing paradigm.
Segments=ordered list of instructions.
Instructions of topological or service based.
The routing is done at the edge (ingress node) which add to the header all the information needed to make the packet reach the destination keeping the core network light weighted and faster since they are also stateless. 


## Introduction to Segment Routing
#### Control Plane 
Supprt:
 - Distributed Scenario: a node individually computes the source-routed policy
 - Centralized Scenario: the SR controller computes the source-routed policies
 - Hybrid Scenario: when outside of a internal getaway protocol(IGP) the SR controller can compute a source-route policy on behalf of the IGP node

#### Data Plane
- over MPLS (multi protocol label switching), with no changing on the forwarding plane
- over IPv6, adding a new header called ==SR Header==(SRH)


#### SR forwarding
SR nodes have a table that specify the actions
Possible actions:
- Push: insertion of a segment at the top of the segment list
- Next: inspect the next segment
- Continue: the current segment is not completed and remain active

## SR Policy
Identified by:
$$<headend, color, endpoint>$$
where:
- headend is the node where the policy is instanciated/implemented
- endpoint indicated the destination of the policy
- color 32-bit that associate the SR Policy with an intent (like use the "use the lowest-latency path available")
#### Candidate Path and Segment List
To move the packet from the headend to the endpoint according to the color, the policy uses the candidate paths

**Candidate paths:** dictates the actual route and is associated with a Segment-List (SID-List)

**Segment-List (SID-List):** specific order sequence of instructions that the packet must traverse to reach the endpoint

Candidate paths can be calculated dynamically or configured explicitly.

The headend node learns about these paths through local configuration or through a centralized entity like a Path Computation Element (PCE).

A single policy can have multiple candidates paths (prioritized by preferences values) and multiple segment lists (which can be assigned different weights to balance traffic load between them)

**Blind SID (BSID):** shourtcut to identify the SR policy installed in the forwarding plane so that the headend receives a packet directed with this BSID it apply the whole segment list to the packet header.


## SRv6 and Segment Routing extension Header

##### SRH Segment routing header
 Inserted in the header by the originating source or by the ingress node when the packet enter the SR domain.
Carries the __Segment list__, 128-bit IPv6 addresses representing the specific topological path of services the packet must traverse.
List placed in reverse order.
__Segment Left__ = act as a counter of the next segment to inspect and determine the packet progress through the network.

#### Node Processing the SRH
only the router whose address correspond to the Destination Address (DA) of the IPv6 of the packet can inspect the SRH. 

__Source node:__ Sets the packet initial DA to the first segment in the list, then set the __Segment Left__ counter, and forward the packet. 

__Non-SR Transit Nodes:__ Due to the packet using an IPv6 a non SR transit node look at the DA and forward the packet and not inspect or alter the SRH.

**SR Segment Endpoints:** Inspect the SRH:
- if the __Segment Left is greater than  0__ decrement, update the DA to the next address in the SL and forward the packet.
- if the __Segment Left is 0__ the packet has reached the end of the segments, remove the SR headers and process the underlying payload.

**SIDs, Functions, and the MyLocalSID Table** Every SRv6-capable node maintains a **MyLocalSID Table** that lists all the local segments (SIDs) explicitly assigned to it.

- **Segment Format:** An SRv6 SID is logically formatted as **LOC:FUNCT**.
    - The **LOC** (locator) part is a routable prefix that guides the packet to the node owning the SID.
    - The **FUNCT** (function) part is an identifier that tells the receiving node exactly what instruction to execute. SIDs can also carry arguments, making the full format `LOC:FUNCT:ARGS`.
- **Key Functions:** Every local SID is bound to an instruction. The most basic is the **End** function, which simply updates the DA with the next segment and forwards the packet. Another is **End.X**, which acts as a layer-3 cross-connect.
- **Advanced Programmability:** This structure allows for immense flexibility. For example, a node can bind a specific local SID to a Virtual Machine (VM), meaning that when a packet hits that segment, it is steered into the VM to have complex, custom functions applied to it

## Network Programming

**1. The Programmable SID Structure (****LOC:FUNCT:ARGS****)** An SRv6 SID is much more than a simple routing address; it represents a specific instruction bound to a node. The chapter emphasizes the `LOC:FUNCT:ARGS` logical format:

- **LOC (Locator):** The routable part of the address that guides the packet to the specific node that owns the SID.
- **FUNCT (Function):** An opaque identifier for the local function that the receiving node must execute (such as `End`, `End.X`, or `End.B6`).
- **ARGS (Arguments):** Optional additional parameters that the function might require to execute properly.

**2. Integrated Network Function Virtualization (NFV)** Because virtually _any_ function can be attached to a local SID, a router can bind a SID directly to a local Virtual Machine (VM). This allows network operators to seamlessly steer packets through complex, custom network applications (like firewalls or traffic analyzers) simply by adding the VM's specific SID to the packet's segment list.

**3. Overlay Networks and SLA Enforcement** Network programming enables the creation of powerful overlay networks that can strictly enforce Service Level Agreements (SLAs) within the underlay network. Instead of relying on standard routing that might choose a congested or slow path, an operator can program a specific "low latency path" for sensitive traffic by utilizing specific segment instructions (like the `End.B6` function).

**4. TI-LFA (Topology Independent Loop-Free Alternate)** Segment Routing provides highly resilient networks with sub-50 millisecond protection against local link, node, or Shared Risk Link Group (SRLG) failures. If a failure occurs, the network can perform an immediate Fast Reroute (FRR) by instantly inserting a new backup segment into the packet to steer it safely around the broken path.