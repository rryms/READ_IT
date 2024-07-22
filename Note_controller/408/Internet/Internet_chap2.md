[Referenced Book](https://book.systemsapproach.org/direct/problem.html)

## Chap2
these five issues—encoding, framing, error detection, reliable delivery, and access mediation

1. The first is encoding bits onto the transmission medium so that they can be understood by a receiving node. 
2. Second is the matter of delineating the sequence of bits transmitted over the link into complete messages that can be delivered to the end node. This is the framing problem, and the messages delivered to the end hosts are often called frames (or sometimes packets). 
3. Third, because frames are sometimes corrupted during transmission, it is necessary to detect these errors and take the appropriate action; this is the error detection problem. 
4. The fourth issue is making a link appear reliable in spite of the fact that it corrupts frames from time to time. 
5. Finally, in those cases where the link is shared by multiple hosts—as is often the case with wireless links, for example—it is necessary to mediate access to this link. This is the media access control problem

This chapter considers these issues in the context of specific network technologies: point-to-point fiber links (for which SONET is the prevalent example); Carrier Sense Multiple Access (CSMA) networks (of which classical Ethernet and Wi-Fi are the most famous examples); fiber-to-the home (for which PON is the dominant standard); and mobile wireless (where 4G is rapidly morphing into 5G).

### terminal