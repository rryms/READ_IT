[reference book](https://book.systemsapproach.org/internetworking/problem.html)
The concept of interconnecting different types of networks to build a large, global network is the core idea of the Internet and is often referred to as internetworking.

subproblems:
1. way to interconnect links. Devices that interconnect links of the same type are often called switches, or sometimes Layer 2 (L2) switches.
2. The core job of a switch is to take packets that arrive on an input and forward (or switch) them to the right output so that they will reach their appropriate destination.
3. Given the enormous diversity of network types, we also need a way to interconnect disparate networks and links (i.e., deal with heterogeneity). Devices that perform this task, once called gateways, are now mostly known as routers, or alternatively, Layer 3 (L3) switches.