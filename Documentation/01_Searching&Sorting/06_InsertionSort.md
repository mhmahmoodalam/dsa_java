# Insertion Sort Algorithm

## Explanation

you compare an element with the element to its left. \
If the element to its left is greater, then you should \
shift the greater element to the right by one position \
and the smaller one to the left. In the next iteration, \
you need to compare this smaller element with the one to \
its left, and shift it if the element to the left is \
greater. You stop when you find that the element to the \
left is smaller than the element with which you are \
comparing it.

```flow

Start
|
|__ Input the array of elements
|
|__ Set n = length of array
|
|__ Repeat from index 1 to n - 1 (outer loop)
|   |
|   |__ Set current element = array[i]
|   |
|   |__ Set j = i - 1
|   |
|   |__ Repeat while j >= 0 and array[j] > current element (inner loop)
|   |   |
|   |   |__ Move array[j] to array[j + 1]
|   |   |
|   |   |__ Decrement j by 1
|   |
|   |__ Place current element in its correct position: array[j + 1] = current element
|
|__ Output the sorted array
|
End

```

## Notes

- compares backward
- Works well for mostly sorted array
- for reverse sorting selection sort work better
- for average case both selection or insertion has same efficiency


## Analysis

Time complexity is n*n

## Problem Statement

Insertion Sort Code

### Description

Write a program in Java that can return an array in descending order of elements using insertion sort.
The program will take the size of the array and the elements of the array as inputs.

### The code should

Sample Input:
4
1
2
3
4
Sample Output:
4
3
2
1

Here, input value ‘4’ (the first input) corresponds to the array size, and the rest of the numbers correspond to the elements of the array.

### Solution

```java

import java.util.Scanner;
 class Source {
  public static void main(String[] args){
      Scanner input = new Scanner(System.in);
      int size = input.nextInt();
      int[] arr = new int[size];
      for(int i =0; i< size;i++){
          arr[i]= input.nextInt();
      }
      int count =0;
      for( int i=0;i<size;i++){
          int v = arr[i];
          int j =i;
          while(j >=1 && arr[j-1]> v){
              count++;
              arr[j] = arr[j-1];
              j--;
          }
          arr[j] =v;
      }
      System.out.println(count);
      for(int i =0; i< size;i++){
          System.out.println(arr[i]);
      }
  }

}


```
