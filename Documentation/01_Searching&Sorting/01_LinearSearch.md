# Linear Search Algorithm

## Explanation

It essentially compares the element that you are searching for with every element
in the array. It keeps comparing until it finds the required element, or till it
reaches the end of the array, to conclude that the element does not exist.

Brute-Force Searching
Brute-force searching is also known as exhaustive searching, and it simply means to check
all possible configurations for a given problem. It is easy to implement and would most
definitely find the solution, although it consumes a lot of time.

Example:

If you have a problem set in a countable space (chess moves are countable, passwords are
countable, continuous stuff is uncountable), then the brute force approach will explore this 
space considering all solutions equally. In the chess example, if you want to checkmate your 
opponent, then this is done through a series of moves, which are countable. Brute force will 
go through all the sequences of moves, however unlikely they may be. The word unlikely is 
important because it means that if you have knowledge of your problem (you know what is 
unlikely to be a solution, for example, sacrificing your queen), then you can do much 
better than applying brute force.

``` flow
Start
|
|__Input the array of elements and the element to search for
|
|__ Set index = 0
|
|__Repeat while index < length of array
|   |
|   |__ If current element at index equals the search element
|   |   |
|   |   |__Return index
|   |
|   |__ Increment index by 1
|
|__If element is not found in the array
|   |
|   |__ Return "Element not found"
|
End
```

For more details, please visit the link given below:

https://stackoverflow.com/questions/8103050/what-exactly-is-the-brute-force-algorithm

## Analysis

The algorithm takes n steps in the worst case. Hence, it follows O(n). 

## Problem Statement

Given an array of non-negative integers, write a code to search the position of an
 element in the array in the reverse order. Do not print anything when the element
  is not present in the given array.

Also, if the key is repeated, print the index where the key is appearing for the 
first time in reverse order.

## The code should

Take the size of the array as an input from the user.
The elements of the array as an input from the user.
The key you are searching for, as an input from the user.

Sample Input:
7
6 8 3 5 9 1 2
9
Sample Output:
2
Here the output is 2 because the position of number 9 is 2 from the reverse order
 as mentioned in the question.

```java
import java.util.Scanner;
class Source{
    public static void main(String args[]){
      Scanner input = new Scanner(System.in);  
      int count = input.nextInt();
      int[] array = new int[count];
        for (int i = 0; i < count; i++) {
           array[i] = input.nextInt();
       }
       int key = input.nextInt();
       input.close();
       
      for(int i = count -1; i >=0 ; i--){
          if(array[i] == key){
              System.out.println(count - i - 1);
              return;
          }
      }
  }
}


```
