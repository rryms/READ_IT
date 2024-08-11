[toc]

# Resources
[web-2021](https://sp21.datastructur.es/)
[text-book_2021](https://joshhug.gitbooks.io/hug61b/content/)
[web-2024](https://sp24.datastructur.es/)
[text-book_2024](https://cs61b-2.gitbook.io/cs61b-textbook)

This note for what?
* 提炼知识点，讲义上有的，过分重复的，取消
* 把数据结构总结好，快速到位
看完视频，一天内完成笔记。
write code important!!!!
# Phase 1: Programming Intensive Introduction to Java
Lec1 to Lec11
**Philosophy**
A sense of abstraction ,why make sense?



## Lecture1. Intro,Hello World Java

### Summary
[offical summary](https://sp21.datastructur.es/materials/lectures/lec1/lec1.html) 
* Intro 
* Course Logistics
* Hello world

### 61B Overview  
* Writing code that runs efficiently
* Writing code efficiently

* TMWLO 
  * small minority to learn: **Intro to new material**
  * vast majority: 
    * **Theory**: discussion,study guide,theory homework
    * **Programming,Tool Usage,Problem Decompostion**: Lab,coding project
    * **Design**: Project
* Course Structure
  * Phase1: Programming Intensive Intro to Java
  * Phase2: Course Structure
  * Phase3: Algorithms and Software Engineering

* Weekly Surveys and Study Guides
  * Study guides for each lecture.

### Intro to Java
* Java and Object Orientation
* Java and Static Typing
* Reflection on Static Typing


## Lecture2. Defining and Using Classes

### Summary
[offical summary](https://sp21.datastructur.es/materials/lectures/lec2/lec2.html)
* Compilation
* Defining and Instantiating Classes
* A Closer Look at Static
  
### Compilation
compile the ``.java`` to ``.class``,which has been type checked

### Defining and Instantiating Classes 
* Object instantiation
  * Classes can contains function and data
  * Classes can be instantiated as objects
* Defining a Typical Class(Terminology)
  * Instance variable
  * Constructor
  * Non-static method__aka. Instance Method
* Instantiating a Class and Terminlology
  * Declaration
  * Instantiation
  * Instantiation and Assignment
  * Declaration, Instantiation and Assignment
  * Invocation
### Static vs. Non-static
* key difference
  * Static invoked by the class name
  * Instance invoked using an instance name
  * Static method cannot access instance variables
* *** Why static Methods? ***
对数据对象的属性命名
something not only is class, but general enough not to be instantiated
* Static vs. Non-static

### Managing Complexity with Helper Methods
* Managing Complexity with Classes and Static Methods 
  * Why use classes and static
    * The reason: To take choices away from the programmer.
      * Fewer choices means fewer ways to do things.
      * Fewer ways to do things often means *less complexity*.

* *** Managing Complexity More Generally ***
IMO,a good foundational computer science course should primarily teach you to properly manage complexity.

  * helper methods
    * Using helper methods lets you formalize the decomposition of large problems into small ones.
    * By focusing mental effort on a single task, there’s less room to make mistakes.


## Lecture3 Testing
### Summary
[offical-summary](https://sp21.datastructur.es/materials/lectures/lec7/lec7)
* A Simple JUnit test
* Testing Philosophty
* Selection Sort
* Simpler JUnit Tests

In the real world, programmers believe their code works because of tests they write themselves.
how to build a program? test...

### Ad Hoc Testing vs. JUnit
* Ad-Hoc Testing is Tedious
* JUnit: A library for Making Testing Easier
  * Syntax 1: ``org.junit.Assert.assertEquals(expected, actual)``
    * Test the expected and output the massages
  * Syntax 2: 
    * Anotate each test with ``@org.junit.Test``
    * Change all test methods to non-static...
    * Use a JUnit runner to run all tests and tabulate results
      * IntelliJ provides a default runner/renderer. OK to delete main.
  * Syntax 3: To avoid this we'll start every test file with:
    * ```java
      import org.junit.Test;
      import static org.junit.Assert.*;
      ```
### Testing Philosophy
* Correctness Tool 1: Autograde
  * Autograder Driven Development(ADD)
* Correctness Tool 2: Unit Tests
  * tests for every unit
  * [Test-Driven Develpment](https://ryantablada.com/red-green-refactor---a-tdd-fairytale/)
* Correctness Tool 3: Integration Testing


**learning**
Junit的具体用法；SFTW


## Lecture 4:References,Recursion,and Lists
* Primitive Types
* Reference Types
* Linked Data Structure

Java中基础类型与class的联系：从0、1建立逻辑的世界；其中总需要更高一级的抽象

### The Golden Rule: Summary
* There are 9 types of variables in Java:
  * 8 primitive types (byte, short, int, long, float, double, boolean, char).
  * The 9th type is references to Objects (an arrow). References may be null.
* In box-and-pointer notation, each variable is drawn as a labeled box and values are shown in the box. 
* The golden rule:
  * ``b = a`` copies the bits from a into b.
  * passing parameters copies the bits

### Note
``is`` in python equivalent to ``==`` in Java
  * check the memory addresses
``==`` in python equivalent to ``.equals`` in Java

### Primitve Types
* bits
* declaring a variable
* Simplified Box Notation
  * Instead of writing memory box contents in binary, we’ll write them in human readable symbols.

### Reference Types
* Reference Types
  * There are 8 primitive types in Java: byte, short, int, long, float, double, boolean, char
  * Everything else, including arrays, is a reference type.
* Class Instantiations
  * Java first allocates a box of bits for each instance variable of the class and fills them with a default value (e.g. 0, null).
  * The constructor then usually fills every such box with some other value.
* Reference Type Variable Declarations
  * Java allocates exactly a box of size 64 bits, no matter what type of object.
  * These bits can be either set to:
    * Null (all zeros).
    * The 64 bit “address” of a specific instance of that class (returned by new)
  * The address: All zero refer to 'null', No zero refer to arrows

* Instantitation of Arrays
  * Declaration and Instantiation of Arrays
  * Assignment of Arrays

* IntList and Linked Data Structure

## Lecture 5: SLLists, Nested Classes, Sentinel Nodes 
### Summary
[offical-summary](https://sp21.datastructur.es/materials/lectures/lec4/lec4)

* From Intlist to SLList
  * The private keyword
  * Nested classes
  * Recursive private helper methods
  * Caching
  * Sentinel nodes

### From IntList to SLList
* Improvement 1: Rebranding and Culling
* Improvement 2: Bureaucracy
  * ```java
      public class SLList {
      public IntNode first;

      public SLList(int x) {
      first = new IntNode(x, null);
      }
      }

    ```
### Public vs. Private Nested Classes
* Implement 3: Access Control
  * Use the ``private`` 
* Implement 4: Nested Class
  * Why Nested Class ? : 
* Static Nested Classes
  * If the nested class never uses any instance variables or methods of the outer class, declare it static.
    * Static classes cannot access outer class’s instance variables or methods
### ``addLast()`` and ``size()``
* Private Recursive Helper Methods
  * To implement a recursive method in a class that is not itself recursive
    * Creat a private recursive helper method 
    * Have the public method call the private recursive helper method.
* Improvement 5: Fast ``size()``
  * caches the size of the list
* Improvement 6a : Representing the Empty List
### Sentinel Nodes
* Tip For Being a Good Programmer: Keep Code Simple
* Improvement 6b: Representing the Empty List Using a Sentinel

* **Invariants**
An invariant is a condition that is guaranteed to be true during code execution (assuming there are no bugs in your code).
  * Invariants make it easier to reason about code:
    * Can assume they are true to simplify code (e.g. addLast doesn’t need to worry about nulls).
    * Must ensure that methods preserve invariants.




Intlist :基础节点与其他；当添加元素时，永远在接触底端 $\rightarrow$ 细节的思考
SLLists:来一个数组！！！

利用抽象来思考问题：rules—————(public\private)

---(Nested Classes)

抽象的思考：结果 而非 过程


## Lecture 6: DLLists,Arrays
### Summary
[offical summary](https://sp21.datastructur.es/materials/lectures/lec5/lec5)
* Doubly Linked Lists
* Generic SLLists
* Arrays
* Arrays vs. Classes

### Doubly Linked List(in brief)
* One Downside of SLLists
  * Inserting at back
* Implement 7. Fast operations on last (.last and .prev)
  * Add backwards links from every node
    * doubly linked list (DLList) 
* Doubly Linked List
  * Double Sentiel
  * Cricular Sentinel
* Improvement 8: Fancier Sentinel Nodes
  * Avoid special cases
    * Add an additional sentBack sentinel at the end of the list.
    * Make your linked list circular (highly recommened for project 1), with a single sentinel in the middle.

### Generic Lists
* Integer Only Lists
* SList
* Generics
  * rules
    * In the .java file **implementing** your data structure, specify your “generic type” only once at the very top of the file.
    * In .java files that use your data structure, specify desired type once:
      * Write out desired type during declaration.
      * Use the empty diamond operator <> during instantiation.
      * When declaring or instantiating your data structure, use the reference type.
        * int: Integer
        * double: Double
        * char: Character
        * boolean: Boolean
        * long: Long
        * etc.
### Arrays
* Getting Memory Boxes
  * **Arrays** are a special kind of object which consists of a **numbered** sequence of memory boxes.
  * To get ith item of array A, use A[i].
  * Unlike class instances which have have **named** memory boxes.

* Arrays
  * Arrays consist of:
    * A fixed integer length (cannot change!)
    * A sequence of N memory boxes where N=length, such that:
      * All of the boxes hold the same type of value (and have same # of bits).
      * The boxes are numbered 0 through length-1.
* Array Basics
* Arraycopy

### 2D Arrays
* Arrays of Array Addresses
* Array Boxes can Contain References to Arrays
 
### Arrays vs. Classes
* Arrays and Classes can both be used to organize a bunch of memory boxes
  * Array boxes are accessed using [] notation.
  * Class boxes are accessed using dot notation.
  * Array boxes must all be of the same type.
  * Class boxes may be of different types.
  * Both have a fixed number of boxes.
* Arrays indices can be computed at runtime
* Class member variable names CANNOT be computed and used at runtime

对世界的表述，多方面的思考


## Lecture 7: Arrays and Resizing vs. SLists

[reading](https://joshhug.gitbooks.io/hug61b/content/chap2/chap25.html)
* A Last Look at Linked Lists
* Naive Arrays Lists
* Resizing Arrays
* Gerneric ALists
* Obscurantism in Java

61C Preview :Ultra fast random access results from the fact that memory boxes are the same size(in bits)
Array 是设定抽象是固有的性质，将DList转化为AList，节省时间——抽象的穿刺
抓住不变量(Invariants)
### A Last Look at Linked Lists
* Doubly Linked Lists

### Naive Array
* Random Access in Arrays
* AList Invariant
  * The position of the next item to be inserted is always size.
  * size is always the number of items in the AList.
  * The last item in the list is always in position size - 1.
* The Abstract vs. the Concrete
* ``removeLast``

###  Resizing Arrays
* Array Resizing
  * Implementation 
    * Performance Problem 1: the factor
    * Performance Problem 2: Memory Efficiency

### Generic ALists
* When creating an array of references to Glorps:
  * ``(Glorp []) new Object[cap];``
  * Causes a compiler warning, which you should ignore.
* Nulling out Deleted Items
  * Java only destroys unwanted objects when the last reference has been lost.
  * Keeping references to unneeded objects is sometimes called loitering.
  * Save memory. Don’t loiter.

### Obscurantism in Java


## Lecture 8: Interface and Implementation Interitance
### Summary
[reading](https://joshhug.gitbooks.io/hug61b/content/chap4/chap41.html)
* The Problem
* Hypernyms,Hyponyms, and Interface Inheritance
* Implementation Inheritance :Default Methods
* Implementation Inheritance :Extends

* Interface vs. Implementation Inheritance
  * Interface Inheritance (a.k.a. what):
    * Allows you to generalize code in a powerful, simple way.
* Implementation Inheritance (a.k.a. how):
  * Allows code-reuse: Subclasses can rely on superclasses or interfaces.
    * Example: print() implemented in List61B.java.
    * Gives another dimension of control to subclass designers: Can decide whether or not to override default implementations.
* **Important**: In both cases, we specify “is-a” relationships, not “has-a”.
  * Good: Dog implements Animal, SLList implements List61B.
  * Bad: Cat implements Claw, Set implements SLList.

### Problem
* keep things in order
* Method Overloading in Java
  * Java allows multiple methods with same name, but different parameters.
### Hypernyms, Hyponyms, and Interface Inheritance
* Hypernyms--对具体的侧面抽象
* Hyponym --- 对抽象的具体
* Interface
  1. Define a reference type for our hypernym (List61B.java).
  2. Specify that SLLists and ALists are hyponyms of that type.

### Overriding vs. Overloading
**重写**vs. **超载**
* Method Overriding
  * has a method with the exact same signature as in the “superclass”
* Method Overriding vs. Overloading
* Overloading
  * Methods with the same name but different signatures are overloaded.
  * Adding the ``@Overriding`` 
    * optional reminder 
      1. if not override, a compile error
      2. help remind

### Interface Inheritance
* Interface Inheritance
  * Specifying the capabilities of a subclass using the implements keyword is known as interface inheritance.
    * Specifies what the subclass can do, but not how.
    * Subclasses must override all of these methods!
* Copying the Bits
  *  When you set x = y or pass a parameter, you’re just copying the bits.
  *  A memory box can only hold 64 bit addresses for the appropriate type.
  * for subclass, is-a relations can hold the address

### Implementation Inheritance: Default Methods
* Implementation Inheritance
  * Java also allows implementation inheritance.
  * Subclasses can inherit signatures AND implementation.
  * Use the **default** keyword to specify a method that subclasses should inherit from an **interface**.

* Overriding Default Methods

### Static and Dynamic Type, Dynamic Method Selection
* Static Type vs. Dynamic Type
  * Every variable in Java has a “compile-time type”, a.k.a. “static type”.
    * This is the type specified at declaration. Never changes!
  * Variables also have a “run-time type”, a.k.a. “dynamic type”.
    * This is the type specified at instantiation (e.g. when using new).
    * Equal to the type of the object being pointed at

* Dynamic Method Selection For Overrideen Methods

### Signature Selection, Dynamic Method Selection
* An Alternate Viewpoint: DMS as a TWO Step
  1. At compile time: We determine the **signature S** of the method to be called.
     * S is decided using **ONLY static types**---using the static type to choose function
     * The signature is the method name and the number and type of its parameters.
  2. At runtime: The dynamic type of the **invoking object** uses its method with this exact signature S.
     * By “invoking object”, we mean the object whose method is invoked.

### Practical Inheritance
### Interface vs. Implementation Inheritance
* Interface vs. Implementation Inheritance
* Dangers of Implementation Inheritance
抽象的层次：
将SLList与AList整合怎么搞
1. overload
2. Interface___overriding

Interface与基本类型的技术化关联：
 

## Lecture 9: Extends,Casting,HigherOrderFunction
### Summary
[reading](https://joshhug.gitbooks.io/hug61b/content/chap4/chap42.html)
* Implementation Inheritance :Extends
* Encapulation
* Casting
* Higher Order Functions in Java
### Implementation Inheritance: Extends
* The Extends Keyword
  * If you want one class to be a hyponym of another class, you use extends.
* Constructor Behavior Is Slightly Weird
  *  Constructors are not inherited. However, the rules of Java say that **all constructors must start with a call to one of the super class’s constructors**[link](https://docs.oracle.com/javase/tutorial/java/IandI/super.html)
  * Calling Other Constructors
    * If you want to use a super constructor other than the no-argument constructor, can give parameters to super.
    * ```java
      super(x);
      deletedItems = new SLList<Item>();

      ```
* The Object Class
  * every type in Java is a descendant of the Object class.
* Is-a vs. Has-a
利用抽象，区分了层级关系(Abstraction Barriers)：``is-a`` or ``has-a``

### Encapsulation
* Complexity: The Enemy
  * Hierarchical abstraction
  * Design for change
* Modules and Encapsulation
* Abstraction Barriers
* Implementation Inheritance Breaks Encapsulation

### Type Checking and Casting
* Reminder: Dynamic Method Selection
  * If overridden, decide which method to call based on run-time type of variable.
* Compile-Time Type Checking
  * Compiler allows method calls based on compile-time type of variable.
* Compile-Time Types and Expressions

* Casting
  * Java has a special syntax for specifying the compile-time type of any expression

### Dynamic Method Selection puzzle
* Static Type vs. Dynamic Type
* Static Methods, Variables, and Inheritance
[doc for hiding](https://docs.oracle.com/javase/tutorial/java/IandI/override.html)
* The rules:
  * Compiler allows memory box to hold any subtype
  * Commiler allows calls based on static types
  * **Overriden non-static methods are seleted at run time based on dynamic type**



### High Order function

## Lec 10: Subtype Polymorphism vs.HoFs 
### Summary
[reading](https://joshhug.gitbooks.io/hug61b/content/chap4/chap43.html)
* Building a General Max Function
  * The Naive Approach
  * OurComparable
  * Compilation Error Puzzle
  * Comparable
* Comparators
To summarize, interfaces in Java provide us with the ability to make callbacks. Sometimes, a function needs the help of another function that might not have been written yet (e.g. max needs compareTo). A callback function is the helping function (in the scenario, compareTo). In some languages, this is accomplished using explicit function passing; in Java, we wrap the needed function in an interface.

### High Order Function vs. Explicit Subtype Polymorphism
* Subtype Polymorphism
  * Polymorphism: “providing a single interface to entities of different types
  *  when call ``deque.addFirst()``, the actual behavior is based on the dynamic type
  *  Java automatically selects the right behavior using what is sometimes called “dynamic method selection”.

### Building a Gerneral Max Function
-----Something are comparable to compare with others
* The Naive Approach
  * Goal: The One True Max Function that returns max of any array regardless of type 
    * Objects cannot be compared to other objects with ``>``
    * Specifical Comparation on Dog---Not Generic
* OurComparable
  * Creat an interface that guarantees a comparison method
    * Have Dog implement this interface.
    * Write Maximizer class in terms of this interface.
  ```java
  public interface OurComparable{
    /** Return negative number if this < o.
     * Return 0 if equals
     * Return postive if ...
    */
    public int compareTo(object o);
  }
  public class Dog implements OurComparable {
   private String name;
   private int size;
    @overrided
   /** Returns <0 if this dog is less than the dog pointed at by o, and so forth. */
   public int compareTo(Object o) {
       Dog uddaDog = (Dog) o;
       return this.size - uddaDog.size;
   }
  }
  public class Maximizer{
    public static OurComparable max(Ourcomparable[] a){
    }
  }
  ```
  * Benefits 
    * No need for array max
    * Code that operates on multiple types (mostly) gracefully
* Compilation Error Puzzle
* Comparable
  * Two issue
    * Awkward casting to/from Objects
    * Not Generic
      * No existing classes implement OurComparable (e.g. String, etc).
      * No existing classes use OurComparable (e.g. no built-in max function that uses OurComparable)
  * Comparable Advantages
    * Lots of built in classes implement Comparable (e.g. String).
    * Lots of libraries use the Comparable interface (e.g. Arrays.sort)
    * Avoids need for casts.
### Comparators
--- A comparative machine
* Additional Orders in Java
  * standard Java approach: Create ``SizeComparator`` and ``NameComparator`` classes that implement the ``Comparator`` interface.
  * code
    ```java
    public class Dog implements Comparable<Dog>{
      private String name;
      private int size;
      public static class NameComparator implements Comparator{
        public int compare(Dog d1, Dog d2){
          return d1.name.compareTo(d2.name);
        }
      }
    }
    Comparator<Dog> cd = new Dog.NameComparator();
    if(cd.compare(d1,d3) > 0){
      d1.bark();
    }else{
      d3.bark();
    }
    ``` 

We can create an interface (``Comparable``)that guarantees that any implementing class, like Dog, contains a comparison method, which we'll call ``compareTo``, in order to solve ``>`` for a more generic compire.

We'll take advantage of an interface that already exists called Comparable. Comparable is already defined by Java and is used by countless libraries. 

### Comparator
What if we'd like to sort Dogs in a different way than their natural ordering, such as by alphabetical order of their name? 
To do this, we can simply defer to String's already defined compareTo method. 


## Lecture 11: Exception,Iterators,Object Methods
### Summary
* **Today’s Goal: ArraySet**
* Iteration
  * The Enhanced For Loop
  * iterator, next, hasNext
  * iterator, next, hasNext for ArraySet
  * Iterable
* Object Methods
  * ``==`` vs. ``equals``
  * toString
  * Better toString (Bonus)
  * .of (Bonus)

### Iteration
* The Enhanced For Loop
  * Java allows us to iterate through Lists and Sets using a convenient shorthand syntax sometimes called the “foreach” or “enhanced for” loop.
* iterator,next, hasNext
  * The enhanced for loop works by first calling the ``.iterator`` method of the object.
  * The ``Interator`` interface has its own API for fetching values one-by-one:
    * hasNext: Tells us whether there are more values.
    * next: gets the next value.
  * How Iteration Really works
    * In that case, we can iterate with either of the two equivalent pieces of code.
    * Left code is shorthand for right code.
    ```java
    /** short hands for iterator */
     for(int x : javaset){
      System.out.println(x); 
     }
    /** the completed version*/
    Iterator<Integer> seer = javaset.iterator();
    while (seer.hasNext()){
      int x = seer.next();
      System.out.println(x);
    }
    ```
* Implementation
  ```java
  public class ArraySet<T> {
   /** returns an iterator (a.k.a. seer) into ME */
   public Iterator<T> iterator() {
       return new ArraySetIterator();
   }

   private class ArraySetIterator implements Iterator<T> {
       private int wizPos;

       public ArraySetIterator() {
           wizPos = 0;
       }

       public boolean hasNext() {
           return wizPos < size;
       }

       public T next() {
           T returnItem = items[wizPos];
           wizPos += 1;
           return returnItem;
       }
   }
  }

  ``` 
* Iterable
  * ``implements Interable<T>``tell that the class was iterable and a iterator inside to use
  * 
### Object Methods
* All classes are hyponyms of Object.
* ``toString()`` 
  * The toString() method provides a string representation of an object.
    * System.out.println(Object x) calls x.toString() 
    [println](https://github.com/AdoptOpenJDK/openjdk-jdk11/blob/999dbd4192d0f819cb5224f26e9e7fa75ca6f289/src/java.base/share/classes/java/io/PrintStream.java#L896) [String.valueOf](https://github.com/AdoptOpenJDK/openjdk-jdk11/blob/f0ef2826d2116f4e0c0ed21f8d54fe9d0706504e/src/java.base/share/classes/java/lang/String.java) which calls toString
  * The [implementation of ``toString()`` in object](https://github.com/AdoptOpenJDK/openjdk-jdk11/blob/999dbd4192d0f819cb5224f26e9e7fa75ca6f289/src/java.base/share/classes/java/lang/Object.java#L245) is the the name of the class, then an @ sign, then the memory location of the object.
  * implements
    ```java
      @Override
      public String toString() {
      StringBuilder returnSB = new StringBuilder("{");
      for (int i = 0; i < size; i += 1) {
       returnSB.append(items[i]);
       returnSB.append(", ");
      }
      returnSB.append("}");
      return returnSB.toString();
      }

    ``` 
* == vs. equals
  ``equals()`` and ``==`` have different behaviors in Java. ``==`` Checks if two objects are actually the same object in memory. Remember, pass-by-value! ``equals()`` checks if two boxes hold the same thing. For primitives, this means checking if the values are equal. For objects, this means checking if the address/pointer is equal.
  * ``this``: Address of Current Object
  * ``instanceOf`` Demo
    * Checks to see if o’s dynamic type is Dog (or one of its subtypes).
      * If no, returns false.
      * If yes, returns true and casts o into a variable of static type Dog called uddaDog.
      * Works correctly, even if o is null.
      ```java
      @override 
      public boolean equals(Object o){
        if(o instanceof Dog uddaDog){
          return this.size == uddaDog.size;
        }
        return false;
      }
      ```
      


