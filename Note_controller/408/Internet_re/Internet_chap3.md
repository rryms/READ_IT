[reference book](https://book.systemsapproach.org/internetworking/problem.html)
The concept of interconnecting different types of networks to build a large, global network is the core idea of the Internet and is often referred to as internetworking.

subproblems:
1. way to interconnect links. Devices that interconnect links of the same type are often called switches, or sometimes Layer 2 (L2) switches.
2. The core job of a switch is to take packets that arrive on an input and forward (or switch) them to the right output so that they will reach their appropriate destination.
3. Given the enormous diversity of network types, we also need a way to interconnect disparate networks and links (i.e., deal with heterogeneity). Devices that perform this task, once called gateways, are now mostly known as routers, or alternatively, Layer 3 (L3) switches.
4. This is particularly the case at the high end, where there seems to be a never-ending need for more switching capacity that can handle the ever-increasing traffic load in the Internet’s core.

## 3.1 Switching Basics
add node for medium,
1. This node would differ from a repeater, which operates on bits, not frames, and just blindly copies the bits received on one interface to another. Instead, this node would fully implement the Ethernet’s collision detection and media access protocols on each interface. 
2. Hence, the length and number-of-host restrictions of the Ethernet, which are all about managing collisions, would not apply to the combined pair of Ethernets connected in this way. This device operates in promiscuous mode, accepting all frames transmitted on either of the Ethernets, and forwarding them to the other.




### Datagrams
### Virtual Circuit Switching
### Source Rountin


## 3.2 Switched Ethernet

### Learning Bridges
### Implementation
### Spanning Tree Algorithm
### Broadcast and Multicast
### Virtual LANs(VLANs)


## 3.3 Internet(IP)
 we saw that it was possible to build reasonably large LANs using bridges and LAN switches, but that such approaches were limited in their ability to scale and to handle heterogeneity. In this section, we explore some ways to go beyond the limitations of bridged networks, enabling us to build large, highly heterogeneous networks with reasonably efficient routing. We refer to such networks as internetworks.
### What is an Internetwork
### Service Model
* an addressing scheme, which provides a way to identify all hosts in the internetwork, 
* a datagram (connectionless) model of data delivery.
#### L2 vs. L3 Networks
#### Datagram Delivery
#### Packet Format

### Global Addresses



### Global Addresses
### Datagram Forwarding in IP
### Subnetting and Classless Addressing

## 3.4 Routing 
### Network as Graph
### Distance-Vector(RIP)
### Link State(OSPF)
### Metrics
