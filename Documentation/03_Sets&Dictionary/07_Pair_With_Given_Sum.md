# Problem Statement

Pair With a Given Sum

You will be given an array of integers and a target sum. You need to check whether there exist any two integers in the array whose sum is equal to the given target sum. If so, then print ‘true’; otherwise, print ‘false’.

## Description

If the given array of integers and the target sum are {1, 7, 40, 8, -7, 3} and 15, respectively, then check whether a pair with the sum equal to the given target sum exists or not.

The output should be ‘true’ because 7 and 8 are the pair of integers from the given array of integers whose sum is equal to the given target sum 15.

## Pseudocode

```pseudocode

- Create a HashSet.
- For each element of the array, carry out the following:
    - Get the difference of the target sum and the array element.
    - If the HashSet contains the difference:
        - Then print ‘true’ and return.
    - Add the array element to the HashSet.
    
```

## Input Output

6 \
1 7 40 8 -7 3 \
15 \

The first input is 'n' that is the size of the input array. The next line of input represents n space-separated integers. The last input is the target sum. The output is true because there exist two integers in the input array whose sum is equal to the target sum that is 7,8.

### Solution

```java

import java.util.*;

class Source
{
    public static void main (String[] args)
    {
        Scanner in = new Scanner(System.in);

        // number of the elements
        int n = in.nextInt();

        int array[] = new int[n];

        //storing the input integers to an array
        for(int i =0;i<n;i++){
            array[i] = in.nextInt();
        }
        
        // getting the target sum from input
        int targetSum = in.nextInt();
        
        //write your code here
        HashSet<Integer> diffset = new HashSet<>();
        for( int i=0;i<array.length;i++){
            int diff = targetSum - array[i];
            if(diffset.contains(array[i])) {
                System.out.println("true");
                return;
            }
            else{
                diffset.add(diff);
            } 
        }
        System.out.println("false");
        
    }
} 


```
