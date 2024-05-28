# Lec6 Synchronization 1: Concurrency and Mutual Exclusion
## Conclusion
* Processes have two parts
     * Threads (Concurrency)
     * Address Spaces (Protection)
* Various textbooks talk about processes 
     * When this concerns concurrency, really talking about thread portion of a process
     * When this concerns protection, talking about address space portion of a process
* Concurrent threads are a very useful abstraction
     * Allow transparent overlapping of computation and I/O
     * Allow use of parallel processing when available
* Concurrent threads introduce problems when accessing shared data
     * Programs must be insensitive to arbitrary interleavings
     * Without careful design, shared variables can become completely inconsistent


# Lec7 Synchronization 2: Concurrency(Con't), Lock Implementation, Atomic Instructions

## Conclusion

* Concurrent threads introduce problems when accessing shared data
     * Programs must be insensitive to arbitrary interleavings
     * Without careful design, shared variables can become completely inconsistent
* Important concept: **Atomic Operations**
     * An operation that runs to completion or not at all
     * These are the primitives on which to construct various synchronization primitives
* Talked about hardware atomicity primitives:
     * Disabling of Interrupts, test&set, swap, compare&swap, load-locked & store-conditional
* Showed several constructions of Locks
     * Must be very careful not to waste/tie up machine resources
         * Shouldn’t disable interrupts for long
         * Shouldn’t spin wait for long
     * Key idea: Separate lock variable, use hardware mechanisms to protect modifications of that variable

# Lec8 Synchronization 3: Locks, Semaphores, Monitors
## Conclusion
* Important concept: Atomic Operations
     * An operation that runs to completion or not at all
     * These are the primitives on which to construct various synchronization primitives
* Talked about hardware atomicity primitives:
     * Disabling of Interrupts, test&set, swap, compare&swap, load-locked & store-conditional
* Showed several constructions of Locks
     * Must be very careful not to waste/tie up machine resources
         * Shouldn’t disable interrupts for long
         * Shouldn’t spin wait for long
     * Key idea: Separate lock variable, use hardware mechanisms to protect modifications of that variable
* Showed primitive for constructing user-level locks 
     * Packages up functionality of sleeping


# Lec9 Synchronization 4: Semaphores(Con't), Monitors and Readers/Writers
## Conclusion
* **Semaphores**: Like integers with restricted interface
     * Two operations:
         * P(): Wait if zero; decrement when becomes non-zero
         * V(): Increment and wake a sleeping task (if exists)
         * Can initialize value to any non-negative value
     * Use separate semaphore for each constraint
* **Monitors**: A lock plus one or more condition variables
     * Always acquire lock before accessing shared data
     * Use condition variables to wait inside critical section
         * Three Operations: Wait(),Signal(), andBroadcast()
* Monitors represent the logic of the program
     * Wait if necessary
     * Signal when change something so any waiting threads can proceed
     * Monitors supported natively in a number of languages
* Readers/Writers Monitor example
     * Shows how monitors allow sophisticated controlled entry to protected code