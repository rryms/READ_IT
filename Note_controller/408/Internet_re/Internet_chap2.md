[Referenced Book](https://book.systemsapproach.org/direct/problem.html)

## Chap2
(datalink layer)数据链路层
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
The problem with the Manchester encoding scheme is that it doubles the rate at which signal transitions are made on the link, which means that the receiver has half the time to detect each pulse of the signal. The rate at which the signal changes is called **the link’s baud rate**. In the case of the Manchester encoding, the bit rate is half the baud rate, so the encoding is considered only 50% efficient. Keep in mind that if the receiver had been able to keep up with the faster baud rate required by the Manchester encoding in Figure 25, then both NRZ and NRZI could have been able to transmit twice as many bits in the same time period


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

1. The idea is to denote the beginning of a frame by sending a special SYN (synchronization) character. The data portion of the frame is then sometimes contained between two more special characters: STX (start of text) and ETX (end of text).
The standard way to overcome this problem by “escaping” the character by preceding it with a DLE (data-link-escape) character whenever it appears in the body of a frame; the DLE character is also escaped (by preceding it with an extra DLE) in the frame body. 
2. 

#### Bit-Oriented Protocols(HDLC)
High-Level Data Link Control(HDLC)

#### Clock-Based Framing(SONET)

### 2.4 Error Detection 
#### 2.4.1 Internet Checksum Algorithm
#### 2.4.2 Cyclic Redundancy Check
 This is referred to as “polynomial arithmetic modulo 2.” Since this is a networking book, not a mathematics text, let’s focus on the key properties of this type of arithmetic for our purposes (which we ask you to accept on faith):
 * Any polynomial$\ B(x) $can be divided by a divisor polynomial $\ C(x)$ 
 if $\ B(x)$is of higher degree than $\ C(x)$.
 * Any polynomial $\ B(x)$ can be divided once by a divisor polynomial $\ C(x)$if $\ B(x)$ is of the same degree as $\ C(x)$ 
* The remainder obtained when $\ B(x)$ is divided by $\ C(x)$ is obtained by performing the exclusive OR (XOR) operation on each pair of matching coefficients.

### 2.5 Reliable Transmission

采用确认和超时重传两种机制的可靠传输协议称为自动重传请求(ARQ)
ARQ协议有三种，停止等待协议、**后退N帧协议和选择重传协议**

#### Stop-and-Wait


#### Sliding Window
连续ARQ协议
* 后退N帧协议(GBN)
* 选择重传协议(SR)


#### Concurrent Logical Channels

### 2.6 Multi-Access Networks
Ethernet eventually became the dominant local area networking technology, emerging from a pack of competing technologies. Today, it competes mainly with 802.11 wireless networks but remains extremely popular in campus networks and data centers. The more general name for the technology behind the Ethernet is **Carrier Sense, Multiple Access with Collision Detect (CSMA/CD)**.

* As indicated by the CSMA name, the Ethernet is a multiple-access network, meaning that a set of nodes sends and receives frames over a shared link. You can, therefore, think of an Ethernet as being like a bus that has multiple stations plugged into it. The “carrier sense” in CSMA/CD means that all the nodes can distinguish between an idle and a busy link, and “collision detect” means that a node **listens as it transmits** and can therefore detect when a frame it is transmitting has interfered (collided) with a frame transmitted by another node.

no more description for CSMA/CD

Modern Ethernet links are now largely point to point; that is, they connect one host to an Ethernet switch, or they interconnect switches. As a consequence, the “multiple access” algorithm is not used much in today’s wired Ethernets, but a variant is now used in wireless networks, such as 802.11 networks (also known as Wi-Fi).

#### 2.6.1 Physical Properties
* A **transceiver**, a small device directly attached to the tap, detected when the line was idle and drove the signal when the host was transmitting. It also received incoming signals. The transceiver, in turn, connected to an Ethernet adaptor, which was plugged into the host. 
* Multiple Ethernet segments can be joined together by **repeaters** (or a multi-port variant of a repeater, called a **hub**). A repeater is a device that forwards digital signals, much like an amplifier forwards analog signals; repeaters do not understand bits or frames. No more than four repeaters could be positioned between any pair of hosts, meaning that a classical Ethernet had a total reach of only 2500 m

#### 2.6.2 Access Protocol 
 This algorithm is commonly called the **Ethernet’s media access control (MAC)**.It is typically implemented in hardware on the network adaptor.  
 * Frame Format

 * Addresses
To summarize, an Ethernet adaptor receives all frames and accepts
1. Frames addressed to its own address
2. Frames addressed to the broadcast address
3. Frames addressed to a multicast address, if it has been instructed to listen to that address
4. All frames, if it has been placed in promiscuous mode


 * Transmitter Algorithm
 the real smarts are implemented at the sender’s side
 Not coincidentally, every Ethernet frame must be at least 512 bits (64 bytes) long: 14 bytes of header plus 46 bytes of data plus 4 bytes of CRC

Once an adaptor has detected a collision and stopped its transmission, it waits a certain amount of time and tries again. Each time it tries to transmit but fails, the adaptor doubles the amount of time it waits before trying again. This strategy of doubling the delay interval between each retransmission attempt is a general technique known as exponential backoff. More precisely, the adaptor first delays either 0 or 51.2 μs, selected at random. If this effort fails, it then waits 0, 51.2, 102.4, or 153.6 μs (selected randomly) before trying again; this is k × 51.2 for k=0..3. After the third collision, it waits k × 51.2 for k = 0..23 - 1, again selected at random. In general, the algorithm randomly selects a k between 0 and 2n - 1 and waits k × 51.2 μs, where n is the number of collisions experienced so far. The adaptor gives up after a given number of tries and reports a transmit error to the host. Adaptors typically retry up to 16 times, although the backoff algorithm caps n in the above formula at 10.


### 2.7 Wireless Networks
#### Basic Issues
* medium efficiently

#### Wi-Fi(802.11)
* using a variant of frequency division multiplexing called orthogonal frequency division multiplexing (OFDM)
##### Collision Avoidance 

##### Distribution System

##### Frame Format
#### Bluetooth(802.15.1)



### phrases

