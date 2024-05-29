# Binary Search Algorithm

## Explanation

for binary search, you need a sorted array. You start at the middle index \
and compare the element that you are searching for with the element at the\
 middle index. If the element at this index does not match the element that \
 you are searching for, then you check whether it is greater or lesser than \
 the element at the index. If it is greater than the element at the middle \
 index, then you discard everything to the left and move to the right. \
 Then you find the middle of this array, which is to the right, compare \
 the required element with its middle and continue doing this until you \
 find the required element.

ideally one would do\
mid = (start + end)/2 \
but for better and enhanced we must always do \
mid = (start+(end-start)/2) 

read here why? \
https://ai.googleblog.com/2006/06/extra-extra-read-all-about-it-nearly.html

```flow

Start
|
|__ Input the sorted array and the element to search for
|
|__ Set left = 0 (index of the leftmost element) and right = length of array - 1 (index of the rightmost element)
|
|__ Repeat while left <= right
|   |
|   |__ Set mid = (left + right) / 2 (calculate the index of the middle element)
|   |
|   |__ If array[mid] equals the search element
|   |   |
|   |   |__ Return mid (element found)
|   |
|   |__ If array[mid] is less than the search element
|   |   |
|   |   |__ Update left = mid + 1 (search the right half)
|   |
|   |__ If array[mid] is greater than the search element
|       |
|       |__ Update right = mid - 1 (search the left half)
|
|__ If element is not found in the array
|   |
|   |__ Return "Element not found"
|
End

```

## Notes

- The array must be sorted for binary search to work
- In the binary search algorithm, after every search operation, the search gets reduced by  1/2
- Alway suse mid = (start+(end-start)/2) for mid calculation
- If array is unsorted linear search is more optimal than binary

## Linear Search vs Binary Search

Suppose you have an unsorted array, and you are told to search for a particular element in it. Since you know that binary search is more efficient than linear search, and since binary search can be applied only on a sorted array, the most efficient way to approach this task is to first sort the array and then apply binary search.

In such a case, we should calculate the efficiency of the entire process. Sorting an unsorted \
array is an O(nlogn) process(MergeSort). Once sorted, applying \
binary search on the array is an O(logn)process. So, the entire process would take steps in the \
order of nlogn + logn, which is more than O(n) as taken by linear search. So, if we have an \
unsorted array and there is no need to sort it, then using linear search is more efficient than \
using binary search.

## Analysis

The Master Theorem is a tool used to solve recurrence relations that arise in the analysis of divide-and-conquer algorithms. The Master Theorem provides a systematic way of solving recurrence relations of the form:

T(n) = aT(n/b) + f(n)

where a, b, and f(n) are positive functions and n is the size of the problem. The Master Theorem provides conditions for the solution of the recurrence to be in the form of O(n^k) for some constant k, and it gives a formula for determining the value of k.

T(n) = T(n/2) + O(1) \
Using maesters thoeram , time complexity = O(logn) \
Best case = O(1) \
Avg/Worstcase = O(log(n))

## Problem - Number of Unsuccessful Attempts

### Description

Write a code that returns the number of unsuccessful attempts made to search for an element in the array using Binary search.

### The code should

Take the size of the array as an input from the user \
The elements of the array as an input from the user \
The key you are searching for as an input from the user \

Sample Input: \
5 \
2 3 4 5 8 \
8 \

Sample Output: \
2 \

So in this sample test case, the first input is the size of the array i.e the array has \
5 elements. Next 5 inputs are the elements inside the array. The last input i.e. 8 is the \
key the code should search for. Since in this case, it will take 2 unsuccessful steps for \
the code to reach 8, so the output is 2.

Hint: To calculate the middle index use the recommended formula instead of using the formula \
used in pseudocode.

### Solution

```java

import java.util.*;
 class Source {
   
   public int getBinarySearchUnsuccessfulComparisonCount(int[] inputArr, int key) {
    int unsuccessfulCount=0;
    int l =0, r=inputArr.length - 1, mid =0;
    while( l<=r){
        mid = l +((r - l)/2);
        if(key == inputArr[mid]) {
            return unsuccessfulCount;
        }
        if(key < inputArr[mid]) {
            r= mid -1;
            ++unsuccessfulCount;
        }
        else if(key > inputArr[mid])  {
            l=mid + 1;
            ++unsuccessfulCount;
        }
    }
    return unsuccessfulCount;
  }
   public static void main(String args[] ) throws Exception {
       Source bs = new Source();
       Scanner scanner = new Scanner(System.in);
       int size = scanner.nextInt();
       int array[] = new int[size];
       for (int i = 0; i < size; i++) {
           array[i] = scanner.nextInt();
       }
       int key = scanner.nextInt();
       System.out.println(bs.getBinarySearchUnsuccessfulComparisonCount(array, key));
   }
}

```
