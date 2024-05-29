# Merge Sort Algorithm

So far the Bubble sort , Insertion Sort and Selection sort were sorting in $n^2$ time complexity

Merge sort takes nlogn time.

## Explanation

Merge sort utilizes ‘divide and conquer’ to sort an array. We keep dividing an array into two halves until we reach the single elements. Once we reach this stage, we start to merge them back in the required order.

### PseudoCode

```flow

Start
|
|__ Input the array of elements
|
|__ Call MergeSort function with the array
|   |
|   |__ If the array has only one element or is empty
|   |   |
|   |   |__ Return the array (base case)
|   |
|   |__ Divide the array into two halves
|   |
|   |__ Call MergeSort for the left half
|   |
|   |__ Call MergeSort for the right half
|   |
|   |__ Merge the sorted left and right halves
|       |
|       |__ Create an empty array to store the merged result
|       |
|       |__ While both left and right arrays have elements
|       |   |
|       |   |__ Compare the first elements of left and right arrays
|       |   |
|       |   |__ Append the smaller element to the result array
|       |
|       |__ Append any remaining elements of left or right arrays to the result array
|   
|__ Output the sorted array
|
End


```
```java
MergeSort(A)
     n=length(A)
     if (n<2) return 
     mid=n/2
     L=A[0...mid-1]
     R=A[mid....n-1]
     for   0<= l <=mid-1
         L[l]=A[l]
     for  mid<= r <=n-1
         R[r-mid]=A[r]
     MergeSort(L) 
     MergeSort(R) 
     Merge(L,R,A)

```

## Notes

- breaks the array into smaller fractions, sort and merge them 
- there can be other versions as well. One of those can be found [here](https://www.geeksforgeeks.org/merge-sort/). 

## Analysis

```maths

T(n) = c + n+ 2T(n/2) + n
     = 2T(n/2) + 2n + c
     = 2[2T(n/4)+ 2(n/2) + c`] + 2n + c
     = 2T(n/4) + 4n + c"
     = 4[2T(n/8) + 2(n/4)+ c"'] + 4n + c"
     = 8T(n/8)+ 6n + C""
     = 2^kT(n/2^k)+ 2Kn + C"""
     = 2^logn T(1) + 2n(logn) + C"""
     = 1 + 2nlogn + c"""
     = nlogn

```

Merge Sort Analysis in Brief

```maths

To analyse the time complexity, we can simply see what divide and conquer can do best to Merge sort to make it efficient.

            1        2        3     ………………………………......................................   n - 1    n                         
 	 	 	 	 	 
Step 1: Divide

For dividing, we will compute the middle of the given ‘n’ number of elements. This would take a constant time, say, D(n) = Θ(1).

Step 2: Conquer

In this step, the sequence of ‘n’ elements is divided into n/2 elements each. And now applying recursion, the n/2 elements would be further divided into n/2, which would continue until a single element is left. Therefore, we are recursively solving two sequences of n/2 elements that give us a time complexity of, say, 2T(n/2).

Step 3: Merge/Combine

Combining the subarrays of ‘n’ elements would take time C(n) = Θ(n). 

T(n) = 0 if n<=1.
T(n) = T(n/2) + T(n/2) + D(n) + C(n) otherwise.

T(n) = 2 * T(n/2) + Θ(n) + Θ(1)

// While finding the Big O /Theta, we ignore the constants; hence, Θ(1) is ignored in the next step. And Θ(n) is taken to be n because even in the worst case, it can have an impact of ‘n’ only.

T(n) = 2 * T(n/2) + n  ………………………………………… (i)

T(n/2) = 2 * (2 * T(n/4) + n/2) = 2^2*T(n/(2^2)) + n   ……………………………… (ii)

// In this step, 'n' in equation (i) is replaced with n/2; therefore, wherever there is n, we have n/2, and when we have n/2, it is replaced with n/4 ([n/2]/2 = n/4), and so on.

T(n) = 2^2 * T(n/2) + 2n ……………………. (iii)

// In this step, ‘n’ in equation (ii) is replaced with 2n to make the same equation of the form T(n).

            .

            .

            .

            .

            .

           = 2^k(2 * T(n/2) + kn

  // Just like equation (iii), we have obtained a general term for T(n)

Suppose n = 2k ; therefore, k=logn.

T(2^k) = nT(n/n) + logn * n

           = n * T(1) + nlogn

But T(1) = 0

T(n) = O(nlogn)

Some relief, isn't it? Merge sort finally brings us out of O(N^2). The efficiency of Merge sort works out to be O(Nlog N). 

```

## Problem - Merge Sort in Decreasing Order

### Description

Write a code that sorts an array in decreasing order using Merge Sort algorithm.

Note that the array in the question which needs to be sorted is named as "randomNumbers". You need to sort the numbers inside the "randomNumbers" array and store the sorted array inside the "sortedNumbers" array.

Input:

- The first input is 'n', that is, the number of elements in the array.
- In the next line, n elements of the array space-separated.

Output:

The array sorted in decreasing order.

### The code should

Sample Test Case-1

Sample Input-1: \
8 \
9 45 76 23 47 1 5 11

Sample Output-1 \
[76,47,45,23,11,9,5,1]

The first input is n (number of elements in the array), here it is 8. The next line in the input represents the elements of the array (space-separated). The output is the same array arranged in decreasing order.

Sample Test Case-2 \
Sample Input-1: \
4 \
1 4 19 3

Sample Output-1 \
[19,4,3,1]

The first input is n (number of elements in the array), here it is 4. The next line in the input represents the elements of the array (space-separated). The output is the same array arranged in decreasing order.

### Solution

```java

import java.util.*;
public class Source {

    public static int[] sort(int[] randomNumbers) {
        return mergeSort(randomNumbers, 0, randomNumbers.length - 1);
    }

    public static int[] mergeSort(int[] numbers, int first, int last) {
        int n = numbers.length;
        while(n < 2) return numbers;
        int mid = first + ( last - first)/2;
        int[] left = new int[mid+1];
        int[] right = new int[mid+1];
        for(int i = 0; i<=mid; i++){
            left[i] = numbers[first + i];
        }
        
        for(int i = 0; mid+i+1<=last; i++){
            right[i] = numbers[mid + i+1];
        }
        
        return merge(numbers,mergeSort(left,0,mid),mergeSort(right,0,mid));
    }

    public static int[] merge(int[] numbers, int[] left, int[] right) {
        int nl = left.length;
        int nr = right.length;
        int l =0,r=0,k=0;
        while(l<nl && r<nr){
            if(left[l]>right[r]){
                numbers[k]=left[l];
                l++;
            }else if (left[l]<right[r]){
                numbers[k]=right[r];
                r++;
            }else {
                numbers[k]=right[r];
                numbers[k]=left[l];
                l++;
                r++;
                k++;
            }
            k++;
        }
        
        while(l<nl){
            numbers[k]=left[l];
                l++;k++;
        }
        while(r<nr){
             numbers[k]=right[r];
                r++;k++;
        }
        return numbers;
    }

    public static void main(String args[]) {
        Scanner scanner = new Scanner(System.in);
        int size = scanner.nextInt();
        int[] randomNumbers = new int[size];
        for (int i = 0; i < size; i++) {
           randomNumbers[i] = scanner.nextInt();
       }
        int[] sortedNumbers;
        sortedNumbers = sort(randomNumbers);
        System.out.println(Arrays.toString(sortedNumbers));
    }
}



```