# Bubble Sort Algorithm

## Explanation

You start with the first two numbers in each \
iteration and perform a comparison between them. \
When the numbers were not in order, you swap them. \
You repeat the same steps for the second and third \ 
numbers, and so on. At the end of the first iteration, \
the largest number is pushed to the end of the array; \
at the end of the second iteration, the second largest \
number is pushed to the second last position, and so on. \

![alt text](image.png)


```flow
Start
|
|__ Input the array of elements
|
|__ Set n = length of array
|
|__ Repeat n - 1 times (outer loop)
|   |
|   |__ Repeat (n - i - 1) times (inner loop)
|   |   |
|   |   |__ If current element is greater than the next element
|   |   |   |
|   |   |   |__ Swap the current element with the next element
|   |   |
|   |
|
|__ Output the sorted array
|
End
```

## Notes

- copying an element is three times as fast as swapping the same element.
- keeping count of swap and exiting when swap count is 0 ensures unnecessary compares

## Analysis

Bubble sort has a time complexity of $O(N^2)$, where N is \
the number of elements in the array. In the first iteration,\
it performs N-1 comparisons; in the second iteration, N-2 \
comparisons; in the third, N-3 comparisons. This continues \
for a total of N iterations. So, the total number of \
comparisons effectively become the sum of the first \
N-1 natural numbers.

total comparisons \
n-1 -> n-2 -> n-3 -> n-4 ......

T(n) = 1 + 2 + ...... + n-1 \
     = n(n+1)/2 \
     = (n-1) * n /2 \
     = O(n*n)

## Problem - Prints the number of swaps

### Description

Write a bubble sort program that prints the number of swaps \
made after M number of iterations (In this case, ‘M’ should \
be an input value).\

For example, if M = 0, the bubble sort program will perform 0 swaps in 0 iterations.

In bubble sort, an iteration is defined as the total number of \
times the outer loop runs. Assume that:\
1) M <= the array size and\
2) the program sorts in descending order.\

### The code should

ask the user to input the values for M, the array size, and \
finally the elements of the array. So, there will be three types\
of inputs — 

Input 1: The value of M \
Input 2: The size of the array \
Input 3: The elements inside the array \

Sample Input: \
2 \
4 \
1 \
2 \
3 \
4

Sample Output: \
5

In this input, the first two numbers denote the values for M \
and  the size of the array, respectively. And rest of \
the numbers denote the elements inside the array.

### Solution

```java

import java.util.Scanner;
  class Source {
   public static int totalBubbleSortSwaps(int[] array, int M) {
       int size = array.length;
       int var = 0;
       int totalSwaps = 0;
       for(int i = 0; i< M; i++){
           for(int j=0;j+1<size-i;j++ ){
               if(array[j] < array[j+1]){
                   int temp = array[j];
                   array[j]= array[j+1];
                   array[j+1]=temp;
                   totalSwaps++;
               }
           }
       }
       return totalSwaps;
   }
   
   public static void main(String[] args){
       Scanner input = new Scanner(System.in);
       int iterationCount = input.nextInt();
       int size = input.nextInt();
       int[] array  = new int[size];
       for( int i =0; i< size; i++){
           array[i] = input.nextInt();
       }
       System.out.println(totalBubbleSortSwaps(array, iterationCount));
   }
   
}

```
