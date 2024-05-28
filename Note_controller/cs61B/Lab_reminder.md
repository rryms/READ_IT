[toc]
# Lab2 JUnit Tests and Debugging
[page](https://sp21.datastructur.es/materials/lab/lab2/lab2#junit-and-unit-testing)
* Conclusion
  * Stepping into, over, and out inside the IntelliJ debugger (this will be handy for projects!)
  * Unit Testing (big picture)
  * JUnit syntax and details
  * Writing JUnit tests
  * Debugging Using JUnit
  * Running the Style Checker
## JUnit and Unit Testing 
```java
@Test
public void testMethod() {
    assertEquals(<expected>, <actual>);
}
    assertTrue(           );
```
# Lab3 Timing Tests and Randomized Comparison Tests
[page](https://sp21.datastructur.es/materials/lab/lab3/lab3)
* Conclusion
  * Empirically measure the time it takes to construct a data structure.
  * Empirically measure the runtime of a data structure’s methods as a function of the size of the data structure.
  * Perform a comparison test between two implementations of a class.
  * Randomly call methods inside of a class.
  * Perform random comparison tests between two implementations of a class.
  * Use the resume button in IntelliJ.
  * Add a condition to a breakpoint.
  * Create an execution breakpoint.
## Timing Tests for List
## Randomized Comparison Tests
* Simple Comparison Test
* Randomized Function Calls
  * ``StdRandom.uniform``
* Conditional Breakpoints
* Adding More Randomized Calls
* Adding Randomized Comparisons

```java
        AListNoResizing<Integer> L = new AListNoResizing<>();

        int N = 500;
        for (int i = 0; i < N; i += 1) {
            int operationNumber = StdRandom.uniform(0, 2);
            if (operationNumber == 0) {
                // addLast
                int randVal = StdRandom.uniform(0, 100);
                L.addLast(randVal);
                System.out.println("addLast(" + randVal + ")");
            } else if (operationNumber == 1) {
                // size
                int size = L.size();
                System.out.println("size: " + size);
            }
        }
```

