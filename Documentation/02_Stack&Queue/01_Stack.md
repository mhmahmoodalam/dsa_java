# Stack

## Explanation

Stack is a FILO | LIFO data structure. It is a linear data structure. There are two linear data structures: \
- Array
- LinkedList
It has below methods:

There is a Stack class in Java, which implements the stack data structure. The class provides the following functions:

- push(object element): It inserts an element to the top of a stack. If stack is full it throws StackOverflowException.
- pop(): It removes an element from the top of a stack. If stack is Empty it throws STackUnderflowException
- isEmpty(): It returns true if a stack is empty; otherwise, it returns false.
- peek(): It returns the element at the top of a stack. It never removes the element
- search(object element): It searches for an element in a stack and returns its location from the top of the stack. If the element is not present in the stack, then it returns ‘-1’.

## Notes

To visualize stacks, you can visit the links given below:

[Array implementation](https://www.cs.usfca.edu/~galles/visualization/SimpleStack.html)

[LinkedList implementation](https://www.cs.usfca.edu/~galles/visualization/StackLL.html)

### Array pseudocode

```java
 class Stack{

    int[] arr;
    int capacity;
    int index;
    public Stack(int capacity){
        arr = new int[capacity];
        this.capacity = capcity;
        index = -1;
    }

    public boolean isEmpty(){
        return index == -1;
    }

    public boolean isFull(){
        return index == capcity -1;
    }

    public void puch(int data){
        if(isfull()){
            return;
        }
        this.arr[++index]= data;
    }

    public int pop(){
        if(isEmpty()){
            return;
        }
        int data = this.arr[index --];
        return data;
    }
 }
```

## Analysis

- each operation takes constant time complexity o(1)

## Problem Statement

Reverse a string

### Description

You are given a string and you have to print the reverse of the string using a stack.

### The code should

Input Format \
A string which has to be reversed. \
Output Format \
The reverse of the input string  \
Sample Input 1: \
abcd \
Sample Output 1: \
dcba \
Sample Input 2: \
abcdef \
Sample Output 2: \
fedcba \

### Solution

```java

import java.util.Scanner;
import java.util.*;

public class Source{
    public static void main(String arg[]) {
        Stack<Character> s = new Stack<Character>();
        Scanner in = new Scanner(System.in);
        String data = in.nextLine();
        for( int i=0; i<data.length(); i++){
            s.push(data.charAt(i));
        }

        while(!s.empty()){
            System.out.print(s.pop());
        }
    }
}


```
