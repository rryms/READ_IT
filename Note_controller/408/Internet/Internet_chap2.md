[Referenced Book](https://book.systemsapproach.org/direct/problem.html)

## Chap2
these five issues—encoding, framing, error detection, reliable delivery, and access mediation

1. The first is encoding bits onto the transmission medium so that they can be understood by a receiving node. 
2. Second is the matter of delineating the sequence of bits transmitted over the link into complete messages that can be delivered to the end node. This is the framing problem, and the messages delivered to the end hosts are often called frames (or sometimes packets). 
3. Third, because frames are sometimes corrupted during transmission, it is necessary to detect these errors and take the appropriate action; this is the error detection problem. 
4. The fourth issue is making a link appear reliable in spite of the fact that it corrupts frames from time to time. 
5. Finally, in those cases where the link is shared by multiple hosts—as is often the case with wireless links, for example—it is necessary to mediate access to this link. This is the media access control problem

This chapter considers these issues in the context of specific network technologies: point-to-point fiber links (for which SONET is the prevalent example); Carrier Sense Multiple Access (CSMA) networks (of which classical Ethernet and Wi-Fi are the most famous examples); fiber-to-the home (for which PON is the dominant standard); and mobile wireless (where 4G is rapidly morphing into 5G).

### Technology Landscape
given you a taste of the diversity of link types that exist and some of the reasons for that diversity

* some physics
  * the medium
  * frequency
* The problem of encoding binary data onto electromagnetic signals
To make the topic more manageable, think it as being divided into two layers.
  * modulation
  * classify links is in terms of how they are used
    * last-mile links(acess networks)
    * long-distance backbone 
      * SONET(Synchronous Optical Network)

* Internet service provider(ISP): an end-user's view of the Internet.
* local area networks(LANs): Ethernet, and its wireless cousin Wi-Fi, are the dominant technologies in this space.

### 2.2Encoding
 **a network adaptor**—a piece of hardware that connects a node to a link. The network adaptor contains a signalling component that actually encodes bits into signals at the sending node and decodes signals into bits at the receiving node

* non-return to zero(NRZ)
Problem: 
1. long strings of 1s or 0s
2. frequent transitions from high to low and vice versa

   * non-return to zero inverted(NRZI)
   * Manchester encoding
   * Differential Manchester

Problems:

### 2.3Framing 
There are several ways to address the framing problem. This section uses three different protocols to illustrate the various points in the design space. 
#### Byte-Oriented Protocols(PPP):Point-to-Point Protocol
to view each frame as a collection of bytes (characters) rather than a collection of bits
* used cases
  *  the Binary Synchronous Communication (BISYNC) protocol developed
  *  the Digital Data Communication Message Protocol (DDCMP) used
* two approaches to byte-oriented framing
  * The first is to use special characters known as sentinel characters to indicate where frames start and end. 
  * The alternative to detecting the end of a frame with a sentinel value is to include the number of bytes in the frame at the beginning of the frame, in the frame header. 

#### Bit-Oriented Protocols(HDLC)

#### Clock-Based Framing(SONET)

### 2.5 Reliable Transmission
#### Stop-and-Wait
#### Sliding Window
#### Concurrent Logical Channels
### 2.6 Multi-Access Networks
Ethernet eventually became the dominant local area networking technology, emerging from a pack of competing technologies. Today, it competes mainly with 802.11 wireless networks but remains extremely popular in campus networks and data centers. The more general name for the technology behind the Ethernet is **Carrier Sense, Multiple Access with Collision Detect (CSMA/CD)**.

#### Access Protocol 
 This algorithm is commonly called the Ethernet’s media access control (MAC).It is typically implemented in hardware on the network adaptor.  
 * Frame Format
 * Addresses
 * Transmitter Algorithm

### phrases

