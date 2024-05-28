# Lec19 Filesystems 1: Performance(Con't), Queueing Theory, Filesystem Design
## Conclusion
* Disk Performance: 
     * Queuing time + Controller + Seek + Rotational + Transfer
     * Rotational latency: on average ½ rotation
     * Transfer time: spec of disk depends on rotation speed and bit storage density
* Devices have complex interaction and performance characteristics
     * Response time (Latency) = Queue + Overhead + Transfer
         * Effective BW = BW * T/(S+T)
     * HDD: Queuing time + controller + seek + rotation + transfer
     * SDD: Queuing time + controller + transfer (erasure & wear)
* Systems (e.g., file system) designed to optimize performance and reliability
     * Relative to performance characteristics of underlying device
* Bursts & High Utilization introduce queuing delays
* Queuing Latency:
     * M/M/1 and M/G/1 queues: simplest to analyze
     * As utilization approaches 100%, latency $\rightarrow \infin$
    $T_q = T_{ser} \times 1/2(1 + C) \times u/(1 - u) $

# Lec20 Filesystems 2: Filesystem Design(Con't), Filesystem Case Studies
## Conclusion
* File System:
     * Transforms blocks into Files and Directories
     * Optimize for access and usage patterns
     * Maximize sequential access, allow efficient random access
* File (and directory) defined by header, called “inode”
* Naming: translating from user-visible names to actual sys resources
     * Directories used for naming for local file systems
     * Linked or tree structure stored in files
* File Allocation Table (FAT) Scheme
     * Linked-list approach 
     * Very widely used: Cameras, USB drives, SD cards
     * Simple to implement, but poor performance and no security 
* Look at actual file access patterns
     * Many small files, but large files take up all the space!
* 4.2 BSD Fast File System: Multi-level inode header to describe files
     * Inode contains ptrs to actual blocks, indirect blocks, double indirect blocks, etc. 
     * Optimizations for sequential access: start new files in open ranges of free blocks, rotational optimization


# Lec21 Filesystems 3: Filesystem Case Studies (Con’t), Buffering, Reliability, and Transactions

## File System Summary
* File System:
     * Transforms blocks into Files and Directories
     * Optimize for size, access and usage patterns
     * Maximize sequential access, allow efficient random access
     * Projects the OS protection and security regime (UGO vs ACL)
* File defined by header, called “inode”
* Naming: translating from user-visible names to actual sys resources
     * Directories used for naming for local file systems
     * Linked or tree structure stored in files
* 4.2 BSD Multilevel Indexed Scheme
     * inode contains file info, direct pointers to blocks, indirect blocks, doubly indirect, etc..
     * NTFS: variable extents not fixed blocks, tiny files data is in header
* File layout driven by freespace management
     * Optimizations for sequential access: start new files in open ranges of free blocks, rotational optimization
     * Integrate freespace, inode table, file blocks and dirs into block group
* Deep interactions between mem management, file system, sharing
     * mmap(): map file or anonymous segment to memory
* Buffer Cache: Memory used to cache kernel resources, including disk blocks and name translations
     * Can contain “dirty” blocks (blocks yet on disk)