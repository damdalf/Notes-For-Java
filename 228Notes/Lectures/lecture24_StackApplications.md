# 228 Notes: **WEEK 9** - Friday

## **Stack Applications:**
***
### **What are the Stack methods?**

* push(E data)
* E pop() throws NoSuchElementException
* E peek() throws NoSuchElementException
* size()
* isEmpty()

### **What are the different ways to implement a Stack?**

* Array implmentation
* Null-terminated singly-linked list
* Doubly-linked list

    * push() - add element
    * peek() - getSize - 1
    * pop() - remove (size - 1)
    * isEmpty() - isEmpty
    * size() - size
***
### **What are stacks used for?**

* Compilers use Stacks to make sense of source code.

    1) Parentheses matching
    
        * Parentheses are well-formed when the opening and closing parentheses, braces, or brackets match.
        * Normal precedence is as follows: [{()}]

***
**How to check if parentheses, braces, and brackets match:**

* Parse a String of parentheses from left to right

1) for each character

    * if opening parentheses
        * push() character
    * if closing parentheses
        * pop() character
        * compare popped parentheses to current parentheses
            * if mismatch, return false
            * if NoSuchElementException, return false

***
### **How to declare a Stack?**
``` java
PureStack<E> stack = new ArrayBasedStack<E>();
```

***
### **What else are Stacks used for?**

* PostFix Notation
    * Notation where two numbers or expressions precede the corresponding operator; or the operator is located POST the numbers or expressions. 
        * No need for parentheses

***
**How to evaluate PostFix Notation:**
* Initialize a Stack
* Parse a String containing a PostFix Notation. 
    * If the character is a number
        * push()
    * If the character is an operator
        * pop() the two numbers from the Stack
        * Compute the leftOperand and the rightOperand
        * Push the results to the stack