# phase 3
* Algorithms
* 3 software engineering lectures
optional textbook---A Philosophy of Software Design
Assignments in this phase:
* Finish Gitlet.
First chance at software engineering and a little design.
* Project 3: Build Your Own World.
Second chance to do some software engineering.
Lots more design practice.
You’ll decide your own task and approach.
Partner project, so try to find a partner soon.

## Lecture 29: Basic Sorts
### Summary
* Goal: Sorting
* The Sorting Problem
* Selection Sort
* Heapsort
  * Naive Heapsort
  * In-Place Heapsort
* Mergesort

### The Sorting Problem
* Java Note
* Sorting: **An Alternate Viewpoint**
  * An **inversion** is a pair of elements that are out of order with respect to ``<``. 
* Performance Definitions
  * Characterizations of the runtime efficiency are sometimes called **the time complexity** of an algorithm.
  * Characterizations of the “extra” memory usage of an algorithm is sometimes called **the space complexity** of an algorithm.
    regradless the initation of space, focus on the using space for the algorithm.

### Selection Sort
* Selection sorting N items: 
  * Find the smallest item in the unsorted portion of the array.
  * Move it to the end of the sorted portion of the array.
  * Selection sort the remaining unsorted items.
* Sort Properties:

### Heapsort
* Naive Heapsort
  * Operation
    * Insert all items into a max heap, and discard input array. Create output array.
    * Repeat N times:
      * Delete largest item from the max heap.
      * Put largest item at the end of the unused part of the output array.
  * Heapsort Runtime Analysis
* In-Place Heapsort
  * Approvement
    * Rather than inserting into a new array of length N + 1, use a process known as “bottom-up heapification” to convert the array into a heap.
      * To bottom-up heapify, just sink nodes in reverse level order.
    * Avoids need for extra copy of all data.
    * Once heapified, algorithm is almost the same as naive heap sort.
  * Operation
    * Heap sorting N items: 
      * Bottom-up heapify input array.
      * Repeat N times:
        * Delete largest item from the max heap, swapping root with last item in the heap.
* Heapsort Runtime


## Lecture 30: Quick Sorts
### Summary 
* Mergesort
* Insertion Sort
  * Naive Insertion Sort
  * In-Place Insertion Sort
  * Insertion Sort Runtime
* Quicksort
  * Quick Backstory, Partitioning
  * Quicksort
### Mergesort
* Using Merge to Speed Up the Sorting Process
  * Merging can give us an improvement over vanilla selection sort:
    * Selection sort the left half: 
    * Selection sort the right half:
    * Merge the results:
* Two Merge Layers
* Mergesort Order of Growth
* Operation
  * Split items into 2 roughly even pieces.
  * Mergesort each half (steps not shown, this is a recursive algorithm!)
  * Merge the two sorted halves to form the final result.
* Complexity
  * 
  * Space complexity with aux array: Costs 
* Top-Down Merge Sort
  * Top-Down merge sorting N items: 
    * Split items into 2 roughly even pieces.
    * Mergesort each half (steps not shown, this is a recursive algorithm!)
    * Merge the two sorted halves to form the final result.
      * **Compare input[i] < input[j] (if necessary).**
      * Copy smaller item and increment p and i or j.
### Insertion Sort
* Naive approach
  * General strategy:
    * Starting with an empty output sequence.
    * Add each item from input, inserting into output at right point.
* In-Place Insertion Sort
  * Inprovement:
    * Do everything in place using swapping instead of move everything over.
  * Operation
    * Designate item i as the traveling item.
    * Swap item backwards until traveller is in the right place among all previously examined items.
    * Performance
      * On arrays with a small number of inversions, insertion sort is extremely fast.
      * Less obvious: For small arrays (N < 15 or so), insertion sort is fastest.

### QuickSort
* Core ideas: Partitioning
* Context for Quicksort's Invention
* Partition
  * To partition an array ``a[]`` on element ``x=a[i]`` is to rearrange a[] so that:
    * x moves to position j (may be the same as i)
    * All entries to the left of x are <= x.
    * All entries to the right of x are >= x.
* Partition Sort, a.k.a. Quicksort
  * Quick sorting N items: 
    * Partition on leftmost item. 
    * Quicksort left half.
    * Quicksort right half.
  * Performance


## Lecture 31: Software Engineering II
### Summary
* Teamwork
* Cast Study in Complexity: Build Your own world
* Modular Design
## Lecture 32: More Quick Sort, Sorting Summary----watch it
### Summary
* Quicksort
  * Quicksort Backstory, Partitioning
  * Quicksort
* Quicksort Runtime Analsis
  * Quicksort Runtime Analysis
  * Avoiding Quicksort Worst Case
* Quicksort Variants
  * Philosophies for Avoiding Worst Case Behavior
  * Quicksort Variant Experiments
* Quick Select(median finding)

### Quicksort Runtime Analysis
* **Quicksort Runtime Analysis**
* Quicksort Performance
* Argument 1. 
* Argument 2 : Quicksort is BST Sort
* 

* **Avoiding Quicksort Worst Case**

### Quicksort Variants
* 
## Lecture 33: Sorting IV: Sorting and Algorithmic Bounds
### Summary
* Goal: How Hard is Sorting?
* Math Problem Warmup
* Theoretical Bounds on Sorting
  * Simple Bounds for TUCS (the ultimate comparison sort)
  * Coin Puzzles
  * Puppy Cat Dog
  * The Sorting Lower Bound
* Sounds of Sorting

## Lecture 34: Software Engineering III
### Summary

## Lecture 35: Sorting V: More Quicksort, Radix Sorts
* Sorting Stability
* Warmup: Digit-by-digit Sorting
* Counting Sort
  * Procedure
  * Runtime
* Radix Sorts
  * LSD Radix Sort
  * MSD Radix Sort
### Counting Sort
* Implementing
  * Count number of occurrences of each item.
  * Iterate through list, using count array to decide where to put everything.
* Runtime

## Lecture 36: Sorting and Data Structures Conclusion
* An Intuitive, Analytical, and Empirical look at Radix vs. Comparison Sorting
* The Just-in-Time Compiler
* Radix Sorting Integers
* Summary
## Lecture 37: Software Engineering IV
### Summary
* Software Engineering 

## Lecture 38: Compression----watchit
### Summary
* Today’s Goal: Compression
* Information Theory
* Prefix Free Codes
* Shannon Fano Codes
* Huffman Coding
  * Core Idea
  * Data Structures for Huffman Coding
  * Huffman Coding in Practice
* Compression Theory
  * Compression Ratios
* LZW Style Compression (Extra)

## Lecture 39: Compression, Complexity, and P=NP
* Models of Compression
* Kolmogorov Complexity
* Space / Time Compression
* P=NP ?
* Is Short = Comprehensible


## Lecture 40: Wrapping Thing UP
* What have Done :61B
* Moving Forwards
