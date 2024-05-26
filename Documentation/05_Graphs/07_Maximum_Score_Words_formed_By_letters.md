# Maximum Score Words Formed by Letters

## Description

Given a list of words, list of single letters (repetition allowed) and score of every character. Return the maximum score of any valid set of words formed by using the given letters(words[i] be unique).

It is not necessary to use all characters in letters and each letter can only be used once. Score of letters 'a', 'b', 'c', ... ,'z' is given by score[0], score[1], ... , score[25] respectively.

## Pseudocode

```pseudocode

```

## Input Output

Input Format:

The first line contains words as String.

The second line contains letters as char.

Then the third line contains the score as numbers.

Output Format:

Print the maximum score as number.

Constraints:

1 <= words.length <= 14
1 <= words[i].length <= 15
1 <= letters.length <= 100
letters[i].length == 1
score.length == 26
0 <= score[i] <= 10
words[i], letters[i] contains only lower case English letters.

Sample Test Cases:

Input

dog cat dad good

a a c d d d g o o

1 0 9 5 0 0 3 0 0 0 0 0 0 0 2 0 0 0 0 0 0 0 0 0 0 0

Output

23

Explanation:

Score  a=1, c=9, d=5, g=3, o=2

Given letters, we can form the words "dad" (5+1+5) and "good" (3+2+2+5) with a score of 23.

Words "dad" and "dog" only get a score of 21.

### Solution

```java

mport java.util.*;
import java.lang.*;
import java.io.*;

public class Source {

    public static int maxScoreWords(String[] words, char[] letters, int[] score) {
        // Add code here
        return helper(0, words, arr, score);
    }
 
    public static int helper(int idx, String[] words, int freq[], int score[]) {
       // Add code here
    }

    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        String str = in.nextLine();
        String[] words = str.split(" ");
        String str1 = in.nextLine();
        char[] tempArr = str1.toCharArray();
        int count = 0;
        for (char i : tempArr) {
            if (i != ' ') {
                count++;
            }
        }
        char[] letters = new char[count];
        int k = 0;
        for (char i : tempArr) {
            if (i != ' ') {
                letters[k++] = i;
            }
        }
        String str3 = in.nextLine();
        String[] arr = str3.split(" ");
        int[] score = new int[arr.length];
        for (int i = 0; i < arr.length; i++) {
            score[i] = Integer.parseInt(arr[i]);
        }
        System.out.println(maxScoreWords(words, letters, score));
    }
}

```
