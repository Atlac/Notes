NFV aims to transform the way that network operators architect and operate networks and network services by evolving standard IT virtualization technology to consolidate many network equipment types onto industry standard high volume servers, switches and storage

#### NFV Infrastructure as a service:

Offers Cloud Computing in addition to network services, CSP Cloud service Provide.
SP need to meet stringent network service performance objectives like latency and reliability.
Since only few SP can provied infrastructure around the globe but the demand is global the IDEA is to run virtualized network functions inside a NFV Infrastructure provided as a service by another SP.


_Cloud Computing Services:_
are tipically offered like:
1. IaaS
2. PaaS
3. SaaS
Offering network connectivity services as a Network as a Service(NaaS)

## How It Works

NFV decouples the network functions (the "work" being done) from the proprietary hardware. It uses virtualization technologies—similar to how a single physical computer can run multiple Virtual Machines (VMs) like Windows and Linux simultaneously.

### The Three Main Components

The architecture is typically broken down into the **NFV Framework**:

1. **VNFs (Virtualized Network Functions):** These are the software versions of network devices. Instead of a physical firewall, you run a **Firewall VNF**.
    
2. **NFVI (NFV Infrastructure):** This is the "soil" where the functions grow. It includes the actual physical servers, storage, and the **hypervisor** (the software that manages the virtual machines).
    
3. **MANO (Management and Orchestration):** This is the "brain" that coordinates everything. It decides when to spin up a new VNF or move one to a different server if the current one is overloaded.


**NFVI:**
Is a network of nodes(called NFVI Point of Presence NFVI-PoP) each virtualizing computation, storage and networking and able to host VNFs.
Nodes are connected through a transport network
elements:
1. hardware platform: is made of all the resources related to a network infrastructure as well as computing and storage resources
2. software platform: is constituted by the:
	1. Virtaulized resources, abstractions of hardware components
	2. Virtualization layer, decouple software from hardware

**Service Plane:**
alone or chained with itself to make more complex NS
a whole VNF can be mapped on a single VM or deployed across multiple NFVI-PoP (nodes).
The interface that is used to provide the interface to the users is called EMS(element management system) and provide the same interface as if it were a physical NF.

##### MANO:
Management and Network Orchestration.
The MANO component allows for **fast**, **scalable** and **dynamic** composition and allocation of VNFs to execute a NS.
objectives:
1. how to compose VNF for a given NS
2. allocate efficiently and schedule VNF of a NS inside NFVI-PoP of underlying NFVI
3. Cenrtalized controll over services provisioning and management

What manags:

1. Virtualized infrastructure Manager: computing storage and networking resources.
2. VNF Manager: manages the virtualized network functions and its life cycle.
3. NFV Orchestrator(NFVO): orchestrate NFVI resources across multiple VMs.


# Virtualization
Most adopted KVM-based VMs:
1. Kernel-based Virtual Machine(KVM) is a virtualization technology built in Linux
2. turn linux into an hypervisor
Hypervisor is a middle-ware that offers a virtual platform to accommodate a variety of guest operating system.
Or Built directly on the HW or Hosted inside a traditional OS.

#### NetVM
built over the KVM platform, remove the overhead when mpving packets between VMs instanciated on the same host machine.
Runs hypervisor user space. memory shared for network data.
Each VM has its own ring to receive and transmit a packet descriptor.


# Migration

1. Optimal placement of VNF
2. optimal migration strategies
Orchestrator is responsible for the allocations.




