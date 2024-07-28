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


### Segment Fault

One very important thing that GDB can do is debug segfaults.

Program received signal SIGSEGV, Segmentation fault.
0x00005555555551f3 in ben (arr=0x7fffffffdcd0, size=10) at ex5_segfault.c:15
15          *ptr = 10;
(gdb) backtrace
#0  0x00005555555551f3 in ben (arr=0x7fffffffdcd0, size=10) at ex5_segfault.c:15
#1  0x00005555555552cc in main () at ex5_segfault.c:33

* size = 10


## Valgrind
[user's manual](https://valgrind.org/docs/manual/manual.html)
### bugs

Even with a debugger, we might not be able to catch all bugs. Some bugs are what we refer to as "**bohrbugs**", meaning they manifest reliably under a well-defined, but possibly unknown, set of conditions. Other bugs are what we call "**heisenbugs**", and instead of being determinant, they're known to disappear or alter their behavior when one attempts to study them. We can detect the first kind with debuggers, but the second kind may slip under our radar because they're (at least in C) often due to mis-managed memory. Remember that unlike other programming languages, C requires you (the programmer) to manually manage your memory.

We can use a tool called Valgrind to help catch to help catch "heisenbugs" and "bohrbugs". Valgrind is a program which emulates your CPU and tracks your memory accesses. This slows down the process you're running (which is why we don't, for example, always run all executables inside Valgrind) but also can expose bugs that may only display visible incorrect behavior under a unique set of circumstances.

### details
`` valgrind ./bork hello``
==10170== Memcheck, a memory error detector
==10170== Copyright (C) 2002-2017, and GNU GPL'd, by Julian Seward et al.
==10170== Using Valgrind-3.13.0 and LibVEX; rerun with -h for copyright info
==10170== Command: ./bork hello
==10170==
==10170== Invalid read of size 1
==10170==    at 0x4C34D04: strlen (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so)
==10170==    by 0x10879F: make_Str (bork.c:22)
==10170==    by 0x108978: translate_to_bork (bork.c:56)
==10170==    by 0x1089F2: main (bork.c:68)
==10170==  Address 0x522f041 is 0 bytes after a block of size 1 alloc'd
==10170==    at 0x4C31B0F: malloc (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so)
==10170==    by 0x108781: alloc_str (bork.c:10)
==10170==    by 0x10895E: translate_to_bork (bork.c:54)
==10170==    by 0x1089F2: main (bork.c:68)
==10170==
==10170== Invalid read of size 1
==10170==    at 0x4C34D04: strlen (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so)
==10170==    by 0x10879F: make_Str (bork.c:22)
==10170==    by 0x108952: translate_to_bork (bork.c:51)
==10170==    by 0x1089F2: main (bork.c:68)
==10170==  Address 0x522f0e2 is 0 bytes after a block of size 2 alloc'd
==10170==    at 0x4C31B0F: malloc (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so)
==10170==    by 0x108781: alloc_str (bork.c:10)
==10170==    by 0x10892D: translate_to_bork (bork.c:48)
==10170==    by 0x1089F2: main (bork.c:68)
==10170==
Input string: "hello"
Length of translated string: 7
==10170== Invalid read of size 1
==10170==    at 0x4C34D04: strlen (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so)
==10170==    by 0x4E9B4A2: vfprintf (vfprintf.c:1643)
==10170==    by 0x4EA2EE5: printf (printf.c:33)
==10170==    by 0x108A6F: main (bork.c:74)
==10170==  Address 0x522f317 is 0 bytes after a block of size 7 alloc'd
==10170==    at 0x4C31B0F: malloc (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so)
==10170==    by 0x108781: alloc_str (bork.c:10)
==10170==    by 0x108833: concat (bork.c:32)
==10170==    by 0x108A15: main (bork.c:69)
==10170==
Translate to Bork: "hefllof"
==10170==
==10170== HEAP SUMMARY:
==10170==     in use at exit: 7 bytes in 1 blocks
==10170==   total heap usage: 11 allocs, 10 frees, 1,051 bytes allocated
==10170==
==10170== LEAK SUMMARY:
==10170==    definitely lost: 7 bytes in 1 blocks
==10170==    indirectly lost: 0 bytes in 0 blocks
==10170==      possibly lost: 0 bytes in 0 blocks
==10170==    still reachable: 0 bytes in 0 blocks
==10170==         suppressed: 0 bytes in 0 blocks
==10170== Rerun with --leak-check=full to see details of leaked memory
==10170==
==10170== For counts of detected and suppressed errors, rerun with: -v
==10170== ERROR SUMMARY: 6 errors from 3 contexts (suppressed: 0 from 0)


1. reading:An invalid read means that your program is reading memory at a place that it shouldn't be (this can cause a segfault, but not always). Size 1 means that we were attempting to read 1 byte.
2.  a good process to follow is to start at high-level details and work our way down (so basically work our way through the call stack that valgrind provides)

``valgrind --leak-check=full ./bork hello``

If we take a look at where we constructed src_str (Str src_str = make_Str(argv[1]);), we can see that it was created using make_str which does not make any calls to allocate space on the heap. The string that we are using to make src_str comes from argv[1]. The program that calls main is responsible for setting up argv[1], so we don't have to worry about it.