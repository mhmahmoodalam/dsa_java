# QuickSort Sort Algorithm

## Explanation

It is another example of divide and conquer. We first identify a pivot and move all elemnts less than pivot to left side and all elemnts gretaher than pivot to write side. Then we recursively do the same quick sort on the left and right sub array. The changes are made on exiting array. No new array is used

```flow

Start
|
|__ Input the array of elements
|
|__ Call QuickSort function with the array and initial indices
|   |
|   |__ If the array has fewer than two elements
|   |   |
|   |   |__ Return the array (base case)
|   |
|   |__ Choose a pivot element (e.g., the last element)
|   |
|   |__ Partition the array around the pivot
|   |   |
|   |   |__ Rearrange the elements so that all elements less than the pivot are on the left
|   |   |   |__ Call Partition function to rearrange the array
|   |   |
|   |   |__ Recursively call QuickSort for the left partition (elements less than pivot)
|   |   |
|   |   |__ Recursively call QuickSort for the right partition (elements greater than pivot)
|   
|__ Output the sorted array
|
End

```

## Notes

- Best case = n log n
- Average Case = nlogn
- Worst Case = n^2
- To prevent the Worst case we can choose random pivot

Read more here\
https://www.geeksforgeeks.org/quicksort-using-random-pivoting/

## PseudoCode

```PseudoCode

Partition ( A, start, end)
    pivot = A[end]
    p = start

    for  start< i < end -1
        if A[i] <= pivot
            Swap(A[i], A[p])
            p++;
    
    Swap(A[p], A[pivot])
    return p;

QuickSort(A, start, end)
    if(start<end)
        p = partition(A,start,end)
    QuickSort(A,start, p-1)
    QuickSort(A,p+1,end)

```

## Analysis

```analysis
partition operation = c + n + c = n + c`

worst case is when the array is already sorted, as we still have to \
run (Swap & recursive call) for all elements. Th p returned will always reduce by one element only for each call.

T(n) = T(n-1) + n \
     = [ T(n-2) + (n-1) ] + n     =  T(n-2) + 2n -1 \
     = [ T(n-3) + (n-2) ] + 2n -1 =  T(n-3) + 3n -3 \
  k  = T(n-k) + nK -k

T(n) = T(n-n) + n * n - n \
     = n^2

Best case:

the best case would be when the pivot can break the array into exactly half arrays.

T(n) = T(n-1) + n \
     = [ T(n/2) + T(n/2) ] + n     =  2^T(n/2) + n \
     = 4^T(n/4) + 2n  
  k  = 2^k * T(n/(2^k)) + nK

T(n) = nlogn
```

## Problem Statement

Quick Sort

### Description

Write a program in Java that takes an array of strings as input  and returns the sorted array. Assume that the sorting needs to  be done based on the size of each string. So, a string with fewer  characters should come before another string with more number of characters. Use the quicksort algorithm for the program.

### The code should

Sample Input - 1:

7 \
Christene \
Tomas \
Marline \
Marcelluss \
Michelle \
Quiana \
Keny 

Sample Output - 1: \
Keny \
Tomas \
Quiana \
Marline \
Michelle \
Christene \
Marcelluss 

So, the first input is the number of elements in the array. \
In this case, the number of elements is 7. Next 7 inputs are  the elements inside the array. As you can see in the output,   the names are sorted as per their length. The name with fewer characters comes before the names with more characters.

Sample Input - 1:
3 \
Cat \
Tree \
Bag 

Sample Output - 2:
Cat \
Bag \
Tree 

So, the first input is the number of elements in the array. In this case, the number of elements is 3. Next 3 inputs are the elements inside the array. As you can see in the output, the names are sorted as per their length. 

Please note that Quick Sort is an unstable sorting algorithm. So, the words with same number of characters may come in a different sequence for different people depending upon the factors outside our control. 

### Solution

```java
import java.util.Scanner;

 class Source {

    public static void swap(String array[], int a, int b){
        String y = array[a];
        array[a]= array[b];
        array[b]=y;
    }
    public static int partition(String array[], int start, int end){
        String pivot = array[end];
        int pointer = start;
        
        for(int i=start; i<end; i++){
            if(array[i].length() <= pivot.length()){
                swap(array,pointer,i);
                pointer++;
            }
        }
        swap(array,pointer,end);
        return pointer;
        
    }
   public static void quickSort(String array[], int left, int right) {
       if (left < right) {
           int position = partition(array, left, right);
           quickSort(array, left, position - 1);
           quickSort(array, position + 1, right);
       }

   }
     //Write your code here

    public static void main(String[] args){
        Scanner input = new Scanner(System.in);
        int size = input.nextInt();
        input.nextLine();
        String[] inputArray = new String[size];
        for(int i=0;i<size;i++){
            inputArray[i] = input.nextLine();
        }
        quickSort(inputArray,0,size-1);
        for(int i=0;i<size;i++){
            System.out.println(inputArray[i]);
        }
    }
}


```
