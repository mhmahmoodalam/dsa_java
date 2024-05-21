# Problem Statement

Check Array of Contiguous Integers

You will be given the array of ‘n’ integers, and you have to print 'true' if it can form a set of contiguous integers from distinct integers in the given 'n' integers. Otherwise, print 'false'.

Note: The given array of integers may contain duplicates.

## Description

Example:

- If the given array of elements is {4, 5, 8, 9, 7, 6, 7, 3, 3}, then the output should be 'true' because the distinct elements  {4, 5, 8, 9, 7, 6, 3} of the array can form a set of contiguous integers {3, 4, 5, 6, 7, 8, 9}.

- If the given array of elements is {4, 8, 9, 7, 6, 7, 3, 3} then the output should be 'false' because the distinct elements  {4, 8, 9, 7, 6, 3} of the array cannot form a set of contiguous integers (we are missing the integer ‘5’ in the range 3–9).

## Pseudocode

Approach 1
Given below is the pseudocode to print true if the distinct integers of the array form contiguous integers; otherwise, print 'false'.

```pseudocode
    - Store all the elements into the array 'elements'.
    - Sort the array in ascending order.
    - For each element of the array, carry out the following:
        - If the next element exists, then take the difference of the next element and the  current element.
        - If the difference is neither 1 nor 0, then print 'false' and return.
    - Print 'true'.
```

Approach 2

```pseudocode
    - Traverse through the array and store each element to the TreeSet. (Note: TreeSet contains only distinct elements and is Sorted)
    - Now, store the first element of the array to temp and get the sum of the following:
        - The number of contiguous integers starting from temp and smaller than temp, and
        - The number of contiguous integers starting from temp+1 and greater than temp+1. -(Hint: You can get this sum using HashSet).
    - If the sum is equal to the size of HashSet, then return 'true'. Otherwise, it returns 'false'.
```

## Input Output

10 \
5 8 4 4 7 6 2 6 7 3 \
The first line of input 10 represents the number of integers that the user will input. The next line in the input is 10 space-separated integers. The output here is true because if we remove all the duplicate integers, the array looks like {5,8,4,7,6,2,3}, which can be rearranged to the array of the contiguous integers {2,3,4,5,6,7,8}.

### Solution

```java

import java.util.*;

class Source {

    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        int n;
        n = in.nextInt();

        //array to store the input elements
        int[] array = new int[n];

        //storing the elements to the array
        for (int i = 0; i < n; i++) {
            array[i] = in.nextInt();
        }

        TreeSet<Integer> treeset = new TreeSet<>();
        for (int i = 0; i < n; i++) {
            treeset.add(array[i]);
        }
        
        int current=0;
        Iterator<Integer> itr = treeset.descendingIterator() ;
        if(!treeset.isEmpty()){
            current =itr.next();
        }else{
            System.out.println("false");
            return;
        }
        while (itr.hasNext()){
                int next = itr.next();
                if((current - next) !=1){
                    System.out.println("false");
                    return;
                }
                current = next;
        }
        System.out.println("true");

    }
}


```
