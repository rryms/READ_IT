see the [lec_note](../../Note_controller/computer_science/cs61c/note/)
# Note_reset
9 lab, 4 proj,写[cs61c_2024](https://cs61c.org/su24/)
# lab0
[**Intro and Setup**](https://web.archive.org/web/20220615223519/https://cs61c.org/sp22/labs/lab00/#gradescope)
* Goals
    * Describe and adhere to all course policies.
    * Set up accounts for GitHub, Gradescope, hive machines, Piazza, and other course-related services.
    * Get familiar with command line tools and Git commands.

## Command Line Essentials
* Shortcut:``Tab``,``Up Arrow``,``Down Arrow``,``Ctrl a``,``Ctrl e``,``Ctrl r``
* ``man``,``ssh``,``scp``

## Fun with Git 
skill till ``git pull -ff`` ``git merge``

## Vim skill
[guide](https://docs.google.com/document/d/1WQF6hQK8CXtlGynSAIX7Rts6q8lykarrqX-zkb9ZDyc/view?pli=1)


# [lab1](https://cs61c.org/su24/labs/lab01/)
* Goals
    * Practice with pointers, strings, and structs
    * Learning basic debugging skills: compiler warnings, assert statement,and GDB

## Pointers

```c
int main(){
    int my_var =20;
    int* my_var_p;
    my_var_p = &my_var;
}

```
* Pointers to Stack vs. Heap

## Arrays
An array is a fixed length data structure that can hold one or more elements of the same type. Unlike lists, arrays do not resize automatically when you add an element.

In C, arrays are represented as a pointer to the first element. Each element of the array is stored in memory and they are stored in contiguous memory locations (side by side). Because arrays are represented only with a pointer to the first element, the pointer itself is not enough to deduce the length of the array. If you need to keep track of the length of an array, you must use another variable.

* Pointer Arithmetic
When performing pointer arithmetic, C automatically accounts for the type of the pointer and adds the correct number of bytes. For example, if you write **ptr + 5**, C will not always add 5 to ptr. Instead, C will add 5 times the size of the datatype that **ptr** points to. If **ptr** was an **int** and **ints** take up 4 bytes in memory, **ptr + 5** adds 20 to the address held in **ptr**.

```c
int array[6]; //request a array sized 6;
array[1] = 3234;
```

## Strings

In C, strings are represented as an array of **char**s. Strings are a special type of **char** arrays because they always end in a null terminator (**\0**). Recall that arrays in C do not contain any information about their length, so the null terminator allows us to determine when the string ends.

When allocating memory for a string, there must be enough memory to store the characters within the string and the null terminator. Otherwise, you might run into undefined behavior. However, the array could be larger than the string it stores.

C has a library of functions for manipulating strings, such as:

* **strlen**: computes the length of a string by counting the number of characters before a null terminator
* **strcpy**: copies a string from one memory location to another, one character at a time until it reaches a null terminator (the null terminator is copied as well)

[double quotes vs. single quotes](https://stackoverflow.com/questions/3683602/single-quotes-vs-double-quotes-in-c-or-c)

* Copying Strings
the use of [strcpy](https://cplusplus.com/reference/cstring/strcpy/)
the use of [strncpy](https://cplusplus.com/reference/cstring/strncpy/): No null-character is implicitly appended at the end of destination if source is longer than num. Thus, in this case, destination shall not be considered a null terminated C string (reading it as such would overflow).

## Struct

* **typedef** vs. struct student.[THIS LINK](https://stackoverflow.com/questions/1675351/typedef-struct-vs-struct-definitions)

* struct 的地址操作-----lec


# lab2 C Debugging

## Compiler Warnings and Errors
read the gcc warnings and errors

## What is GDB
[GDB website](https://www.gnu.org/software/gdb/)
[mannal](https://sourceware.org/gdb/current/onlinedocs/gdb.html/)
GDB, the GNU Project debugger, allows you to see what is going on 'inside' another program while it executes -- or what another program was doing at the moment it crashed.

GDB can do four main kinds of things (plus other things in support of these) to help you catch bugs in the act:


* Start your program, specifying anything that might affect its behavior.
* Make your program stop on specified conditions.
* Examine what has happened, when your program has stopped.
* Change things in your program, so you can experiment with correcting the effects of one bug and go on to learn about another.

GDB commands


## Valgrind

### bugs

Even with a debugger, we might not be able to catch all bugs. Some bugs are what we refer to as "bohrbugs", meaning they manifest reliably under a well-defined, but possibly unknown, set of conditions. Other bugs are what we call "heisenbugs", and instead of being determinant, they're known to disappear or alter their behavior when one attempts to study them. We can detect the first kind with debuggers, but the second kind may slip under our radar because they're (at least in C) often due to mis-managed memory. Remember that unlike other programming languages, C requires you (the programmer) to manually manage your memory.

We can use a tool called Valgrind to help catch to help catch "heisenbugs" and "bohrbugs". Valgrind is a program which emulates your CPU and tracks your memory accesses. This slows down the process you're running (which is why we don't, for example, always run all executables inside Valgrind) but also can expose bugs that may only display visible incorrect behavior under a unique set of circumstances.