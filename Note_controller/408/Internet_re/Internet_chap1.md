[Referenced book](https://book.systemsapproach.org/foreword.html)
思路脉络，后边加共识

# Books_reading
## Chap1
First, it explores the requirements that different applications and different communities of people place on the network. 
Second, it introduces the idea of a network architecture, which lays the foundation for the rest of the book. 
Third, it introduces some of the key elements in the implementation of computer networks. 
Finally, it identifies the key metrics that are used to evaluate the performance of computer networks.
### 1.2 Requirements
An application programmer would list the services that his or her application needs: for example, a guarantee that each message the application sends will be delivered without error within a certain amount of time or the ability to switch gracefully among different connections to the network as the user moves around.

A network operator would list the characteristics of a system that is easy to administer and manage: for example, in which faults can be easily isolated, new devices can be added to the network and configured correctly, and it is easy to account for usage.

A network designer would list the properties of a cost-effective design: for example, that network resources are efficiently utilized and fairly allocated to different users. Issues of performance are also likely to be important.
* Scalable Connectivity
A system that is designed to support growth to an arbitrarily large size is said to scale. Using the Internet as a model, this book addresses the challenge of scalability

* **Physical links**
  * point-to-point
  * multiple-access

Those nodes that are attached to at least two links run software that forwards data received on one link out on another. If organized in a systematic way, these forwarding nodes form a switched network.

* **Switched network**
    * circuit switched
    * packet switched
* packet switched
  * each block of data called a packet or a message
Packet-switched networks typically use a strategy called store-and-forward.

In this situation, a set of independent **networks (clouds)** are interconnected to form an internetwork, or internet for short. 

A node that is connected to two or more networks is commonly called a router or gateway, and it plays much the same role as a switch—it forwards messages from one network to another.

#### 1.2.3 Cost-Effective Resource Sharing
the key requirement

* multiplexing
  * synchronous time-division multiplexing(STDM)
  * frequency-division multiplexing(FDM)
  * statistical multiplexing
To account for this need, statistical multiplexing defines an upper bound on the size of the block of data that each flow is permitted to transmit at a given time. This limited-size block of data is typically referred to as a **packet**, to distinguish it from the arbitrarily large message that an application program might want to transmit.

The decision as to which packet to send next on a shared link can be made in a number of different ways.
To a rounter, there is a issue how to make a firely decision---
* FIFO
* round-robin manner 

**congested**: the switch is forced to buffer these packets in its memory, then overflow.

#### 1.2.4 Support for Common Services

 we view the network as providing logical channels over which application-level processes can communicate with each other;

 * **Identify Common Communication Patterns**
   * File Transfer Protocol(FTP)
   * Network File System(NFS)
   * that independent of exactly what functionality a given channel provides
     * the packet switches 
     * the end hosts(devices)
* **Reliable Message Delivery**
  * There are three general classes of failure that network designers have to worry about. 
    * Bit errors
    * lost packets
    * the problem with the node and link level

### 1.3 Architecture
* the OSI(7-layer) architecture 
* the Internet architecture
the abstract objects that make up the layers of a network system are called **protocols**. 

Each protocol defines two different interfaces
1. it defines a service interface to the other objects on the same computer that want to use its communication services. 
2. Second, a protocol defines a peer interface to its counterpart (peer) on another machine. 

Sometimes it refers to the abstract interfaces—that is, the operations defined by the service interface and the form and meaning of messages exchanged between peers, and sometimes it refers to the module that actually implements these two interfaces.(refer to the former as a protocol specification)

### 1.5 Performance


## Perequirment
*  the cloud is one of the most important icons of computer networking. In general, we use a cloud to denote any type of network, whether it is a single point-to-point link, a multiple-access link, or a switched network.
*  We adopt the Internet’s convention of referring to a generic internetwork of networks as a lowercase i internet, and the TCP/IP Internet we all use every day as the capital I Internet. 