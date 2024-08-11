## Phase 2 : Data Structures
* Incredibly important and foundational material: Expect an CS job interview to lean heavily on this part of the course.
* One programming HWs (HW1) and one exam-prep theory HW (HW2).
  * Applications and deeper insight into data structures.
* One very large solo project (Proj 2), due 4/2. Checkpoint due 3/12.
* Labs:
  * Lab 5: Peer review on project 1.
  * Two labs that implement data structures (hash table and BST).
  * Remaining labs are focused on project 2.



## Lecture 12: Command Line Programming and Data Structures Preview

* public static void main(String[] args)
* Command line compilation and execution
* Git Case Study: Maps, Hashing, Serializable

Along the way we got a brief look at 4 different unrelated topics:
* Maps: Same as a Python dictionary.
git构建的方式；
* Hashing: Representing an object by a sequence of (160) bits.
* Serialization: Saving and loading Java objects from a file.
* Graphs: Generalization of a Linked List.
Will talk about Maps, Hashing, and Graphs in much more detail in later lectures.



## Lecture 13: Introduction to Asymptotic Analysis
### Summary 
[offical summary]([offical summary](https://sp21.datastructur.es/materials/lectures/lec13/lec13)))
* Intuitive Runtime
* Detailed Analysis of Worst Case Order of Growth
* Simplified Analysis
* Big Theta Notation
* Big O Notation

* Summary
  * $$\ C(x)$$

Efficiency comes in two flavors:
  * Programming cost (course to date. Will also revisit later).
    * How long does it take to develop your programs?
    * How easy is it to read, modify, and maintain your code?
      * More important than you might think!
      * Majority of cost is in maintenance, not development!
  * Execution cost (from today until end of course).
    * How much time does your program take to execute?
    * How much memory does your program require?
### Intuitive Runtime Characterizations
* Techniques for Measuring Computational Cost

* Asymptotic Behavior

### Worst Case: Order of Growth
* Simplification Summary
  1.  Only consider the worst case.
  2.  Pick a representative operation (a.k.a. the cost model).
  3.  Ignore lower order terms.
  4.  Ignore multiplicative constants.


## Lecture 14:Disjoint Sets
### Summary
[offical summary]()
* Dynamic Connectivity and the Disjoint Sets Problem
* Quick Find
* Quick Union
* Weighted Quick Union
* Path Compression (CS170 Preview)

*** A Summary of Our Iterative Design Process ***
And we’re done! The end result of our iterative design process is the standard way disjoint sets are implemented today - quick union and path compression.

The ideas that made our implementation efficient:
* Represent sets as connected components (don’t track individual connections).
  * ListOfSetsDS: Store connected components as a List of Sets (slow, complicated).
  * QuickFindDS: Store connected components as set ids.
  * QuickUnionDS: Store connected components as parent ids.
    * WeightedQuickUnionDS: Also track the size of each set, and use size to decide on new tree root.
    * WeightedQuickUnionWithPathCompressionDS: On calls to connect and isConnected, set parent id to the root for all items seen.





## Lecture 15: Asymptotics II Analysis of Algorithms
### Summary
* Review of Asymptotic Notation
* Examples 1-2: For Loops
* Example 3: A Basic Recurrence
* Example 4: Binary Search
* Example 5: Mergesort

## Lecture 16: ADTs and BSTs
### Summary
[offical summary](https://sp21.datastructur.es/materials/lectures/lec16/lec16)
* Abstract Data Types
* Binary Search Tree (intro)
* BST Definitions
* BST Operations
* Sets vs. Maps, Summary

* Abstract data types (ADTs) are defined in terms of operations, not implementation.

* Several useful ADTs: Disjoint Sets, Map, Set, List.
  * Java provides Map, Set, List interfaces, along with several implementations.

* We’ve seen two ways to implement a Set (or Map): ArraySet and using a BST.
  * ArraySet: Θ(N) operations in the worst case.
  * BST: Θ(log N) operations in the worst case if tree is balanced.

* BST Implementations:
  * Search and insert are straightforward (but insert is a little tricky).
  * Deletion is more challenging. Typical approach is “Hibbard deletion”. 

### Abstract Data Types
* Interfaces vs. Implementary
* Abstract Data Types
* Collections
  * Among the most important interfaces in the java.util library are those that extend the Collection interface (btw interfaces can extend other interfaces).
    * Lists of things
    * Sets of things
    * Mappings between items
* Java Libraries


### Binary Search Trees
### BST Definitions 
* Tree 
  * A tree consists of
    * A set of nodes
    * A set of edges that connect nodes
* Rooted Trees and Rooted Binary Trees
* Binary Search Trees
  * A binary search tree is a rooted binary tree with the BST property.

### BST Operstion: Search
* Finding a searchKey in a BST
* BST Search
### BST Operation: Insert
* Inserting a New Key into a BST

### BST Operation: delete
* deleting from a BST
  * Deletion key has no children
  * Deletion key has one children
  * Deletion key has two children

### Sets vs. Maps, Summary
看着Maps是一个一一对应的集合没太大的联系，但是Insight：It's tree connection


## Lecture 17: B-trees
### Summary
[offical summary](https://sp21.datastructur.es/materials/lectures/lec16/lec16)
* BST Performance
* Big O != Worst Case
* 2-3-4 and 2-3 Tree Operations(B-Trees)
* B-Tree Bushiness Invarinants
* B-tree Performance

* BSTs have best case height Θ(log N), and worst case height Θ(N).
  * Big O is not the same thing as worst case!

* B-Trees are a modification of the binary search tree that avoids Θ(N) worst case.

  * Nodes may contain between 1 and L items.
  * contains works almost exactly like a normal BST.
  * add works by adding items to existing leaf nodes.
  * If nodes are too full, they split.
  * Resulting tree has perfect balance. Runtime for operations is O(log N).
  * Have not discussed deletion. See extra slides if you’re curious.
  * Have not discussed how splitting works if L > 3 (see some other class).
  * B-trees are more complex, but they can efficiently handle ANY insertion order.



### BST Tree Height
* The Usefulness of Big O
* BST Height
  * Θ(log N) in the best case (“bushy”).
  * Θ(N) in the worst case (“spindly”).
### Height, Depth, and Performance
* Height and Depth 
  * The depth of a node is how for it is from the root 
  * The height of a tree is the depth of its deepest leaf
  * The “average depth” of a tree is the average depth of a tree’s nodes.
    * determine the average case runtime
  * 
### B-trees/2-3 trees/2-3-4 trees
* Avoiding Imbalance through Overstuffing
* Revising Overstuffed Tree Approach: Move Item up
  * Set a limit L on the number of items,
  * If any node has more than L items, give an item to parent.
    * Pulling item out of full node splits it into left and right.
* Revising Our Overstuffed Tree Approach: Node Splitting
* What Happens If The Root Is Too Full --- split root
  * Perfect Balance
    * If we split the root, every node gets pushed down by exactly one level.

* **The Real Name For Splitting Trees is "B Trees"**
  * B-trees of order L=3 (like we used today) are also called a 2-3-4 tree or a 2-4 tree. 
  * B-trees of order L=2 are also called a 2-3 tree.

* A note on Terminology 
  * Small L
    * simple balanced search tree
  * Large L
    * practice for databases and filesystems

### B-Tree Bushiness Invariants
* Invariants
  * All leaves must be the same distance from the source.
  * A non-leaf node with k items must have exactly k+1 children.
    * guarantee the tree will be bushy
### B-Tree Runtime Analysis


### 2-3 Tree Deletion

## Lecture 18: Red Black Trees
* 2-3 tree hard to implement
  * Maintaining different node types.
  * Interconversion of nodes between 2-nodes and 3-nodes.
  * Walking up the tree to split nodes.

### Summary
[offical summary](https://sp21.datastructur.es/materials/lectures/lec18/lec18)
* Tree Rotation 
* Left Leaning Red-Black Trees
* Maintaining Correspondence Through Rotation

### BST Structure and Tree Rotation
* BSTs
  * The specific BST you get is based on the insertion order.
  * More generally, for N items, there are [Catalan(N)](https://en.wikipedia.org/wiki/Catalan_number) different BSTs.

* Tree Rotation Definition
  * ``rotateLeft(G)``: Let x be the right child of G. Make G the new left child of x.
    * Preserves search tree property. No change to semantics of tree.
    * Detail:
      * Can think of as temporarily merging G and P, then sending G down and left.
* Rotation for Balance
  * Can shorten (or lengthen) a tree
  * Preserves search tree property
  * Rotation allows balancing of a BST in O(N) moves.

### Red-Black Trees
* Search Trees
  * **Binary search trees**: Can balance using rotation, but no algorithm
  * **2-3 trees**: Balanced by construction
* Goal: Build a BST that is structurally identical to a 2-3 tree.
* Representing a 2-3 Tree as a BST: Dealing with 3-Nodes
  * Creat a dummy "glue" nodes
  * Create “glue” links with the smaller item **off to the left**.
* Left-Leaning Red Black Binary Search Tree (LLRB)
  * A BST with left glue links that represents a 2-3 tree 
  * was normal BSTs;
  * There is a 1-1 correspondence between an LLRB and an equivalent 2-3 tree.
  * The red is just a convenient fiction. Red links don’t “do” anything special.
* Problems 1: invalid LLRB
  * break the rules: 2-3 tree and the left leaning
* Problems 2: leave
  * The height
    * 3 nodes double the length
    * an LLRB has no more than ~2x the height of its 2-3 tree.
* LLRB Properties
  * No node has two red links [otherwise it’d be analogous to a 4 node, which are disallowed in 2-3 trees].
  * Every path from root to ~~a leaf~~(a null reference) has same number of **black links** [because 2-3 trees have the same number of links to every leaf]. LLRBs are therefore balanced.
* LLRB Construction
  * Insert as usual into a BST.
  * Use zero or more rotations to maintain the 1-1 mapping.

### Maintain 1-1 Correspondence Through Rotations
* The 1-1 Mapping
* Design Task 1: Insertion Color
* Design Task 2: Insertion on the Right
* Design Task 3: Double Insertion on the Left
* Design Task 4: Splitting Temporary 4-Nodes

* When inserting: Use a red link.
  * If there is a right leaning “3-node”, we have a **Left Leaning Violation**.
    * __Rotate left__ the appropriate node to fix.
  * If there are two consecutive left links, we have an **Incorrect 4 Node Violation**.
    * __Rotate right__ the appropriate node to fix.
  * If there are any nodes with two red children, we have a **Temporary 4 Node**.
    * __Color flip__ the node to emulate the split operation.
* Cascading Balance
  * We have a right leaning 3-node (B-S). We can fix with rotateLeft(b).

### LLRB Runtime and Implementation

#### Search Tree Summary
* Search Trees
  * **Binary search trees** are simple, but they are subject to imbalance.
  * **2-3 Trees (B Trees)** are balanced, but painful to implement and relatively slow.
  * **LLRBs** insertion is simple to implement (but delete is hard).
    * Works by maintaining mathematical bijection with a 2-3 trees.
  * Java’s [TreeMap](https://docs.google.com/presentation/d/1S27xlCPX0Up8WAHZPBqmbcrcKo4FNbyG6eTHamOxzgA/edit#slide=id.g5240c8ba42_0_1469) is a red-black tree (not left leaning).
    * Maintains correspondence with 2-3-4 tree (is not a 1-1 correspondence)
    * Allows glue links on either side (see [Red-Black Tree](https://en.wikipedia.org/wiki/Red%E2%80%93black_tree)).
    * More complex implementation, but significantly (?) faster.

* Other self balancing trees: AVL trees, splay trees, treaps, etc. There are at least hundreds of different such trees.
* 

## Lecture 19: Hashing
### Summary
[slide](https://docs.google.com/presentation/d/1zflCuz_kENAP3VvurKJ0VsusEbejn5AZZIaoiNU14Xo/edit?usp=sharing)
[offical summary](https://sp21.datastructur.es/materials/lectures/lec20/lec20)
* Set Implementations, DataIndexedIntegerSet
* Integer Representations of Strings, Integer Overflow
* Hash Tables and Handling Collisions
* Hash Table Performance and Resizing 
* Hash Tables in Java

* Hash Tables in Java
  * Data is converted into a hash code.
  * The hash code is then reduced to a valid index.
  * Data is then stored in a bucket corresponding to that index.
  * Resize when load factor N/M exceeds some constant.
  * If items are spread out nicely, you get Θ(1) average runtime

### Data Indexed Arrays
* Sets
  * ArraySet
  * BST
  * 2-3 Tree
  * LLRB
* Limit of Search Tree Based Sets
  * require items to be comparable.
  * for better performance


### DataIndexedEnglishWordSet
* Generalizing the Idea
* Avoiding Collisions
* The Decimal Number System vs. Our System for Strings
* Using Data as an Index 
  * Uniqueness
  * Implementing englishToInt

### DataIndexedStringSet
* ASCII Characters
* Implementing asciiToInt
* Going Beyond ASCII
  * Unicode

### Integer Overflow and Hash Codes
* Major Problem : Integer Overflow
  * Consequence of Overflow: Collisions
* Hash Codes and the Pigeonhole Principle
  * [hash code](https://mathworld.wolfram.com/HashFunction.html)
    * a hash code “projects a value from a set with many (or even an infinite number of) members to a value from a set with a fixed number of (fewer) members.”
    * our target set is the set of Java integers, which is of size 4294967296.
  * [Pigeonhole principle](https://en.wikipedia.org/wiki/Pigeonhole_principle)
    * if there are more than 4294967296 possible items, multiple items will share the same hash code.
  * two fundamental challenges
    * collision handling
    * computing a hashCode
    * Separate Chaining Performance
    * Saving Memory Using Separate Chaining and Modulus
    * The Hash Table
      * Data is converted by a hash function into an integer representation called a hash code. 
      * The hash code is then reduced to a valid index, usually using the modulus operator

### Hash Table Performance


### Hash Table: Handling Collisions
* Resolving Ambiguity
* The Separate Chaining Data Index Array
* Separate Chaining Performance
  

## Lecture 20: Heaps and PQs
### Summary[2024-version](https://docs.google.com/presentation/d/1XVJfoSYH2ItiD1rz9yvyEf_HelejbfkYxQgukbgclSY/edit#slide=id.g2174b714862_0_14)
[offical summary](https://sp21.datastructur.es/materials/lectures/lec21/lec21)
* Priority Queue Introduction
  * Intro the Priority Queue
  * Using a PQ
  * Some Bad Implementations
* Heaps
  * Heap Definitions
  * Heap Add
  * Heap Delete
* Tree Representations
  * Recursive Representation
  * Array Representations
* Priority Queue Summary
* Data Structures Summary


### Priority Queues
* The Priority Queue Interface
```java
/** (Min) Priority Queue: Allowing tracking and removal of the
  * smallest item in a priority queue. */
public interface MinPQ<Item> {
	/** Adds the item to the priority queue. */
	public void add(Item x);
	/** Returns the smallest item in the priority queue. */
	public Item getSmallest();
	/** Removes the smallest item from the priority queue. */
	public Item removeSmallest();
	/** Returns the size of the priority queue. */
	public int size();
}
/** Specifical Interface to return the small item in set */

```
* Usage
  * If only want to perceive the biggest items in a huge numbers items, use PQ to delete the smallest items instead of sort everything
    * Save the space
* Bad Implementations
  * Ordered Array---Bad Performance to sort
  * Bushy BST---Hard to solve the same items  
  * HashTable---Also as Bushy BST
### Heaps
* Intro the Heap
  * Binary min-heap:Binary tree that is complete and obeys min-heap property.
    * Min-heap: Every node is less than or equal to both of its children
    * Complete: Missing items only at the bottom level (if any), all nodes are as far left as possible.
* Heap Add---Support one property first, and fix other 
  * Add to end of heap temporarily
  * Swim up the hierarchy to your rightful place  
* Heap Delete
  * Delete min --- the root of the tree
  * Swap the last items in the heap into the root
  * The sink your way down the hierarchy, yielding to most qualified folks..
  * 
* Heap Operations Summary
### Tree Representations
* Tree Representations
  * 1a. Fixed Number of Links(one per child)_Create mapping from node to children
    ```java
    public class Tree1A<Key>{
      Key k;
      Tree1A left;
      Tree1A middle;
      Tree1A right;
      ...
    }
    ```
  * 1b. Array of child links_Create mapping from node to children.
    ```java
    public class Tree1B<Key> {
      Key k; // e.g. 0
      Tree1B[] children;
   ...
   }
    ```
  * 1c. FirstBorn/Sibling Links 
  ```java
  public class Tree1C<Key> {
   Key k; // e.g. 0
   Tree1C favoredChild;
   Tree1C sibling;
   ...
  }
  ```
  * 2. Array of Keys, Array Structure_: Store keys in an array. Store parentIDs in an array.
  ```java
  public class Tree2<Key>{
    Key[] keys;
    int[] parents; // represents the parents' index of current index
  }
  public parent(int k){
    return (k-1)/2;// or just computer it
  }
  ```


### Data Structure Summary
* Search Data Structures(The particularly abstract ones)
* Data Structures
  * A particular way of organizing data.



## Lecture 21: Tree and Graph
### Summary 
[offical summary](https://sp21.datastructur.es/materials/lectures/lec23/lec23)
* Tree Traverals
* Graphs
* Depth First Search 
* Breadth First Search

* Graphs are a more general idea than a tree.
  * A tree is a graph where there are no cycles and every vertex is connected.
  * Key graph terms: Directed, Undirected, Cyclic, Acyclic, Path, Cycle.

* Graph problems vary widely in difficulty. 
  * Common tool for solving almost all graph problems is traversal.
  * A traversal is an order in which you visit / act upon vertices.
  * Tree traversals:
    * Preorder, inorder, postorder, level order.
* Graph traversals:
  * DFS preorder, DFS postorder, BFS.
* By performing actions / setting instance variables during a graph (or tree) traversal, you can solve problems like s-t connectivity or path finding.

### Trees and Traversals
* Tree Definition
  * A tree consist of
    * a set of nodes
    * A set of edges that connect those nodes.
* Rooted Trees Definition
  * Every node N except the root has exactly one parent, defined as the first node on the path from N to the root.
  * A node with no child is called a leaf.
  * terminology: root, child, parent
* Tree Travelsal Orderings
  * Level Order
  * Depth First Traversals
    * 3 types: Preorder, Inorder, Postorder
* A Useful Visual Trick(for Humans)
* The Traversals's goods
  * Preorder Traversal for printing directory listing
  * Postorder Traversal for gathering file sizes

### Graphs
* Trees and Hierarchical Relationships
* Graph Definition
  * A set of nodes.
  * A set of zero or more edges, each of which connects two nodes.
  * No edges that connect a vertex to itself, i.e. no “loops”.
  * No two edges that connect the same vertices, i.e. no “parallel edges”.
* Graph Types
  * Acyclic,Cyclic; Undirected;With Edge Labels
#### Graph Terminology
* Graph:
  * Set of **vertices**, a.k.a. **nodes**.
Set of **edges**: Pairs of vertices.
Vertices with an edge between are **adjacent**.
Optional: Vertices or edges may have **labels** (or **weights**).
A **path** is a sequence of vertices connected by edges.
A **simple path** is a path without repeated vertices.
A **cycle** is a path whose first and last vertices are the same.
A graph with a cycle is ‘cyclic’.
Two vertices are **connected** if there is a path between them. If all vertices are connected, we say the graph is connected.

### Graph Problems
* Graph Queries More Theoretically
* Graph Problem Difficulty

### Depth-First Traveral
* s-t Connectivity
  * one possible algorithm
    1. Mark s. **avoit loop**
    2. Does s == t? If so, return true.
    3. Otherwise, if connected(v, t) for any unmarked neighbor v of s, return true.
    4. Return false.
* Depth First Traversal
  * This idea of exploring a neighbor’s entire subgraph before moving on to the next neighbor is known as Depth First Traversal.
* The Power of Depth First Search
  * computes a path to every vertex.
### Tree vs. Graph Traversals
* Tree Traversals
* Graph Traversals
  * DFS Preorder
  * DFS Postorder
  * BFS order: Act in order of distance from s.
    * breadth first search


## Lecture 22: Graph Traversals and Implementations
[slide](https://docs.google.com/presentation/d/1v5pLls6n5weicMenk_CXxNVC-9O-Uic1usRQYrdxBN0/edit?usp=sharing)   
[offical summary](https://sp21.datastructur.es/materials/lectures/lec24/lec24)
### Summary
* BreadthFirstPaths
* Graph API
* Graph Representations and Graph Algorithm Runtimes
* Graph Traversal Runtimes
* Layers of Abstraction

* BSF : Uses a queue instead of recursion to track what work needs to be done.

* Graph API: We used the Princeton algorithms book API today.
  * This is just one possible API. We’ll see other APIs in this class.
  * Choice of API determines how client needs to think in order to write code.
    * e.g. Getting the degree of a vertex requires many lines of code with this choice of API. 
    * Choice may also affect runtime and memory of client programs.

* Adjacency matrix
* List of edges
* Adjacency list
* 

### BreadthFirstPaths
* Shortest Path Challenge
  * somehow visited in BFS order
* BFS Answer
  * **Breadth First Search**.
    * Initialize a queue with a starting vertex s and mark that vertex.
      * A queue is a list that has two operations: enqueue (a.k.a. addLast) and dequeue (a.k.a. removeFirst).
      * Let’s call this the queue our **fringe**.
    * Repeat until queue is empty:
      * Remove vertex v from the front of the queue.
      * For each unmarked neighbor n of v: 
        * Mark n.
        * Set edgeTo[n] = v (and/or distTo[n] = distTo[v] + 1).
        * Add n to end of queue.


### Graph API
* Graph Decision 1: Integer Vertice
### Graph Representation and Graph Algorithms Runtimes
* Graph Representation
  1. Adjacency Matrix
  2. Edge Sets : Collection of all edges
  3. Adjacency lists
* Graph Printing Runtime

* Graph Representations
* 
### Graph Traversal Implementation and Runtime
### Layers of Abstraction
* how API influence the performance

## Lecture 23: Shortest Paths
### Summary
* Shortest Paths
  * Summary So For: DFS vs. BFS
  * Dijkstra's Algorithm
  * Dijkstra's Correctness and Runtime
  * A*
  * A* Heuristics

* Single Source, Multiple Targets:
  * Can represent shortest path from start to every vertex as a shortest paths tree with V-1 edges.
  * Can find the SPT using Dijkstra’s algorithm.
* Single Source, Single Target:
  * Dijkstra’s is inefficient (searches useless parts of the graph).
  * Can represent shortest path as path (with up to V-1 vertices, but probably far fewer).
  * A* is potentially much faster than Dijkstra’s.
    * Consistent heuristic guarantees correct solution.

### Dijkstra's Algorithm
* Problem: Single Source Single Target Shortest Paths
  * Find the shortest paths from __source__ vertex s to some __target__ vertex t.
  * Observation: 
    * Solution will always be a path with no cycles(no-negtive)
    * Solution will always be a **tree**. 
      * Can think of as the union of the shortest paths to all vertices.
* SPT Edge Count
  * If G is a connected edge-weighted graph with V vertices and E edges, how many edges are in the **Shortest Paths Tree (SPT)** of G
    * V-1.
* Finding a Shortest Paths Tree Algorithmically
  * look the nodes comparing the distance to the end
  * Demo
    * Insert all vertices into fringe PQ, storing vertices in order of distance from source.
    * Repeat: Remove (closest) vertex v from PQ, and relax all edges pointing from v.

### Dijkstra's Correctness and Runtime
* **Dijkstra**'s
  * PQ.add(source,0)
  * For other vertices v, PQ.add(v,infinity)
  * While PQ is is not empty:
    * p = PQ.removeSmallest()
    * Relax all edges from p
* **Relaxing** an edge p → q with weight w:
* If distTo[p] + w < distTo[q]:
  distTo[q] = distTo[p] + w
  edgeTo[q] = p
  PQ.changePriority(q, distTo[q])
* key invariants:
  * edgeTo[v] is the best known predecessor of v.
  * distTo[v] is the best known total distance from source to v.
  * PQ contains all unvisited vertices in order of distTo.
* Important properties:
  * Always visits vertices in order of total distance from source.
  * Relaxation always fails on edges to visited (white) vertices.


* Guaranteed Optimality

* Negative Edges
* Dijkstra's Algorithm Runtime

### A*
加一个变量，减少计算
**watch the video**


## Lecture 24: Minimum Spanning Trees(最小生成树)---watch it
### Summary
* MST, Cut Property, Generic MST Algorithm
* Prim's Algorithm
* Kruskal's Algorithm

### Spannign Trees
* Definition
  * a **spanning tree** T is a subgraph of G, where T :
    * Is connected(make it a tree)
    * acyclic
    * Includes all of the vertices.(spanning)
  * A **minimum spanning tree** is a spanning tree of minimum total weight.
* MST vs. SPT 
  * the MST sometimes happens to be an SPT for a specific vertex
* A Useful Tool for Finding the MST: Cut Property
  * A **cut** is an assignment of a graph’s nodes to two non-empty sets.
  * A **crossing edge** is an edge which connects a node from one set to a node from the other set.
  * **Cut property**:Given any cut, minimum weight crossing edge is in the MST.
* Cut Property in Action
* Cut Property Proof
* Generic MST Finding Algorithm
### Prim's Algorithm
* Start from some arbitrary start node.
  * Repeatedly add shortest edge (mark black) that has one node inside the MST under construction.
  * Repeat until V-1 edges.
* Prim's vs. Dijkstra's
* Prim's Implementation
* Prim's Algotithm Runtime
### Kruskal's Algorithm
* Initially mark all edges gray.
  * Consider edges in increasing order of weight.
  * Add edge to MST (mark black) unless doing so creates a cycle
  * Repeat until V-1 edges.



## Lecture 25: Range Searching and Multi-Dimensional Data
### Summary
* Multi-Dimensional Data
  * Range-Finding and Nearest (1D Data)
  * Multi-Dimensional Data Example
  * QuadTrees for 2D Data
  * KdTrees for Higher Dimensional Data
  * Uniform Partitioning
### Range-Finding and Nearest
* Search Trees
    * Binary Search Tree
    * 2-3 Tree/ 2-3-4 Tree/ B-Tree
    * Red Black Tree
  * support very fast operations
    * Requires that compariable data
    * Use ``Comparable`` interface 
* Expanding the Power of our Set
* Implementing Fancier Set Operations with a BST
* Sets and Maps on 2D Data
### Multi-dimensional Data
* Building Trees of Two Dimensional Data
* Spatial Partitioning/ Rectangle Intersection Interpretation
### QuadTrees
* The QuadTree
  * Every Node has four children
* QuadTree Range Search 
* 
### Higher Dimensional Data
* 3D Data
* Even Higher Dimensional Space
* K-d Trees
* K-d Trees and Nearest Neighbor
* Nestest Pseudocode
### Uniform Partitioning
### Summary and Applicaitons
* Multi-Dimensional Data Summary
* Set operations can be more complex than just contains, e.g.:
Range Finding: What are all the objects inside this (rectangular) subspace?
Nearest: What is the closest object to a specific point?
Note: Can be generalized to k-nearest.

The most common approach is **spatial partitioning**:
Quadtree: Generalized 2D BST where each node “owns” 4 subspaces.
K-d Tree: Generalized k-d BST where each node “owns” 2 subspaces.
Dimension of ownership cycles with each level of depth in tree.
Uniform Partitioning: Partition space into uniform chunks.

## Lecture 26: Prefix Operations and Tries
### Summary
* Tries
* Trie Implementation and Performance
* Alternate Child Tracking Strategies
* Trie String Operations
* Autocomplete

* Tries Summary

### Tries
* Abstract Data Types vs. Specific Implementations
* BST and Hash Table Set Runtimes
* 
### Tries Implementation and Performance
### Alternate Child Tracking Strategies
### Trie String Operations
### Autocomplete


## Lecture 27: Software Engineering I

## Lecture 28: Reduction and Decomposition
### Summary
利用已知问题，及数学上的，逻辑上的推演，简化新问题
[offical-summay]()
* Topological Sorting 
* Shortest Paths on DAGs
* Longest Paths
* Reductions

### Topological Sorting
* Simple solution
  * Simple recursion with indegree 0
* Reduction
  * Perform a DFS traversal from every vertex with indegree 0, NOT clearing markings in between traversals.
    * Record DFS postorder in a list
    * Topological ordering is given by the reverse of that list (reverse postorder)
* better topological algorithm:
  * Run DFS from an arbitrary vertex.
  * If not all marked, pick an unmarked vertex and do it again.
  * Repeat until done.
* Directed Acyclic Graphs
  * A topological sort only exists if the graph is a directed acyclic graph (DAG).

### Shortest Paths on DAGs

### Longest Paths
* A Note on "Mathematical Maturity"
  * [wiki](https://en.wikipedia.org/wiki/Mathematical_maturity)

### Reduction