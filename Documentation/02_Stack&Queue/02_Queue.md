# Queue

## Explanation

Queue is a FIFO | LILO data structure. It is a linear data structure (right -to -left). There are two linear data structures: \
- Array
- LinkedList

It has below methods:
- Enqueue ( adding to queue from one end)
- Dequeue ( removing from another end)

## Notes

- each operation happens in constant time o(1)
- a flat array leads to exhaustion of space with enque and deque operations as at some point the rear & front will keep increasing and reach the end of array

- we can fix this by using circular queue

- this does not happen with LinkedLists
- A queue can be implemented using two stacks and a Stack can be implemented using two queues.
- Unlike Stack, which is a class in Java, Queue is an interface that often needs to be implemented as a linked list.
- In Java there is also PriorityQueue which is direct implementation of Queue, whereas the Linked list implementation is a Deque implementation

- Read more on java in collection interface [here](https://docs.oracle.com/javase/tutorial/collections/interfaces/queue.html).

To visualize stacks, you can visit the links given below:

[Array implementation](https://www.cs.usfca.edu/~galles/visualization/QueueArray.html)

[LinkedList implementation](https://www.cs.usfca.edu/~galles/visualization/QueueLL.html)

### Queue in Java

```java
 Queue<Integer> queue = new LinkedList<Integer>();

 //enqueue
 queue.add(5); // this will throw exception if Queue is already full
 queue.offer(5) // does not throw exception

 //peek
 queue.elemnt(); //return the elements which added first and still present. Throws exception if queue is empty
 queue.peek(); // Same as above but returns null instead of exception if empty

 //Deque
 queue.remove();// this removes the elements added in FIFO order . If queue is empty this will throw exception
 queue.poll(); //same as above but instead of exception return null

```

### Array pseudocode

```java
 class ArrayQueue{

    int[] arr;
    int capacity;
    int front;
    int rear;
    public Stack(int capacity){
        arr = new int[capacity];
        this.capacity = capcity;
        front= rear = -1;
    }

    public boolean isEmpty(){
        return front == -1;
    }

    public boolean isFull(){
        //return front == capacity - 1;
        return front % (capacity -1) == rear;
    }

    public void enqueue(int data){
        if(isfull()){
            return;
        }
        front = (front + 1) % capacity
        if(rear == -1) rear=0;
        this.arr[front]= data;
    }

    public int deque(){
        if(isEmpty()){
            return;
        }
        int data = this.arr[rear];
        if(front ==rear){
            front = rear =-1;
            return data;
        }
        rear = (rear + 1) % capcity
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
