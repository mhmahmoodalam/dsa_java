# Problem Statement First Unique Character

You will be given a string, and you have to find and print the first unique character, i.e., the first non-repeating character of the string.

> The string may contain duplicate characters.

Example:

If the given string is ‘abcdebadf’, then the first unique character is c. If you observe the given string:
    - The first character ‘a’ is repeated abcdebadf.
    - The second character ‘b’ is repeated abcdebadf.
    - The third character ‘c’ is not repeated abcdebadf.

Therefore, the first unique character, i.e., the first non-repeating character of the string, is ‘c’.

## Description

Algorithm:

Note: ‘arr’ is the array of pairs

```pseudocode

    - Input String: Take the input string.
    - Initialize Hashmap: Create an empty Hashmap ( since we need to maintain the order of characters we should use LinkedHashMap)
    - Traverse String: Loop through each character in the input string.
    - Update Hashmap: For each character:
        - Check if the character exists in the Hashmap.
        - If it doesn't exist, add it to the Hashmap with a value of 1.
        - If it does exist, increment its value by 1.
    - Find First Unique Character:     
        - Loop through the input string again.
        - For each character, check its count in the Hashmap.
        - Return the first character with a count of 1.
    - Output Unique Character: Output the first unique character found.

```

### Solution

```java

import java.util.*;

public class Source {

    public static void main(String arg[]) {

        Scanner in = new Scanner(System.in);

        //storing the input string to String variable "str"
        String str = in.nextLine();
        //write your code here
        
        HashMap<Character,Integer> map = new LinkedHashMap<>();
        for( int i=0;i<str.length();i++){
            char ch = str.charAt(i);
            if(map.containsKey(ch)){
                map.replace(ch,map.get(ch)+1);
            }else {
                map.put(ch,1);
            }
        }
        boolean uniqueFound=false;
        for (Character key : map.keySet()) {
            if(map.get(key) == 1){
                System.out.println(key);
                uniqueFound = true;
                break;
            }
        }
        if(!uniqueFound){
            System.out.println(-1);
        }
        

    }
}

```

