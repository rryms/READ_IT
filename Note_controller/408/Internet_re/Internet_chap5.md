[reference_book](https://book.systemsapproach.org/e2e/problem.html)
Once interconnected, the next problem is to turn this host-to-host packet delivery service into a process-to-process communication channel. This is the role played by the transport level of the network architecture, which, because it supports communication between application programs running in end nodes, is sometimes called the end-to-end protocol.


The following list itemizes some of the common properties that a transport protocol can be expected to provide:
* Guarantees message delivery
* Delivers messages in the same order they are sent
* Delivers at most one copy of each message
* Supports arbitrarily large messages
* Supports synchronization between the sender and the receiver
* Allows the receiver to apply flow control to the sender
* Supports multiple application processes on each host

Different transport protocols employ different combinations of these algorithms. This chapter looks at these algorithms in the context of four representative services
* a simple asynchronous demultiplexing service, 
* a reliable byte-stream service, 
* a request/reply service, 
* a service for real-time applications.

1. the Internet’s User Datagram Protocol (UDP) 
2. Transmission Control Protocol (TCP)
3. Remote Procedure Call (RPC) service 
4. the Real-Time Transport Protocol (RTP)