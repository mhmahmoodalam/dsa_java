# Problem Statement Find Symmetric Pair

You will be given an array of pairs, and you have to print all the symmetric pairs. Pair (a, b) and a pair (c, d) are called symmetric pairs if a is equal to d and b is equal to c.

Example:

If the given array of pairs is {{1, 2}, {2, 3}, {3, 4}, {4, 3}, {2, 1}}, then the symmetric pairs in the given array of pairs are (1, 2) and (3, 4) because the pair (1, 2) has its symmetric pair (2, 1), and the pair (3, 4) has its symmetric pair (4, 3) in the given array.

## Description

Algorithm:

Note: ‘arr’ is the array of pairs

```pseudocode

    for(int i = 0; i < arr.length; i++) // Traverse through the given array
        int firstC = arr[i][0]; // Get the first and second elements of the current pair
        int secondC   = arr[i][1];
        for(int j = i+1; j < arr.length; j++) // Check whether the pairs are symmetric to the current pairs or not
            int secondO = arr[j][1];
            int firstO = arr[j][0];
            if(firstO == sec && secondO == first) //If the current pair is symmetric to the other pair, then print the current  pair
                Print the current pair

```

### The code should

Suppose you are given an array of pairs, and you have to print all the symmetric pairs. Pair (a, b) and pair (c, d) are called symmetric pairs if a is equal to d and b is equal to c.

The input will be in the following format:

- The first line will be ‘n’, indicating the size of the input array, i.e., the number of pairs in the array.
- The next ‘n’ lines indicate the ‘n’ pairs.
- Each line will be includes two space-separated integers, indicating the first and the second element of the pair.

The output should be in the following format:

- Print all the first pairs of the symmetric pairs, each in a new line.
- Every line should be two space-separated integers, indicating a symmetric pair.

Note:

- If a pair is symmetric, then print the pair that appears first in the array.
- If there are no symmetric pairs, then print ‘No Symmetric pair’.
- If the array is empty, then consider that there are no symmetric pairs in the array.

Sample input-1: \
4 \
1 2 \
3 4 \
2 1 \
4 3

Sample output-1: \
1 2 \
3 4 \

Sample input-1: \
3 \
1 2 \
2 3 \
3 4

Sample output-1: \
No Symmetric pair

### Solution

```java

import java.util.*;

class Source {

    public static void main(String arg[]) {
        Scanner in = new Scanner(System.in);

        //number of pairs in the array
        int n = in.nextInt();
        int arr[][] = new int[n][2];

        // store the input pairs to an array "arr"
        for (int i = 0; i < n; i++) {
            arr[i][0] = in.nextInt();
            arr[i][1] = in.nextInt();
        }

        HashMap<Integer,Integer> map = new HashMap<>();
        // Write your code here
        boolean symmetryPair=false;
        for(int i =0;i<n;i++){
            if(map.containsKey(arr[i][1]) && map.get(arr[i][1]) == arr[i][0]){
                symmetryPair=true;
                System.out.println(arr[i][1]+" "+map.get(arr[i][1]));
            }else{
                map.put(arr[i][0],arr[i][1]);
            }
        }
        if(!symmetryPair)
        System.out.println("No Symmetric pair");

    }
}

```
