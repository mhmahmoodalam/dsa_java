# Identify a Palindromic String

A palindrome is a word, string, phrase or sentence that reads the same when read backward as well as forward. For example, 'MALAYALAM'.  Since queues and stacks are one of the most frequently used data structures for storing and modifying information, you should create an algorithm to check whether or not the characters of the input string form a palindrome, using either stacks or queues.

## Analysis with stack

The time and space complexity of the algorithm to identify palindrome using stacks is O(n) and O(n^2), respectively. This is because there are two loops used in the solution. One loop would push the characters of the input string, and the other would pop and add those elements to the reversed string for comparison. To do this, a stack and a variable string are used, which are occupying extra memory here.

The stack should be able to store all the ‘n’ characters of the string; therefore, for the stack, you require O(n) space. A variable string is also used in the solution, and the characters from the stack are popped and added to the string one by one. In Java, String is immutable, which means every time a character is added, a new string, which stores the modified string, is created. Hence, a new string of length ‘n’ will be created for all ‘n’ characters of the input string. Therefore, space complexity is O(n^2) for the variable string. The total space complexity of the solution would be O(n)+O(n^2) ~ O(n^2).

## Analysis with Queue

The code will contain two separate loops. The ‘for’ loop would push all the characters of the string in the queue, and the ‘while’ loop would compose a reversed string out of the elements dequeued from the queue. Since the loops are not nested, the time complexity of both the loops is O(n). In the program, you need to have an extra queue as well as a string variable and both of them need space. The size of the queue and the variable string should be large enough to store all the ‘n’ characters of the input string. The queue would take O(n) space and the variable string would take O(n^2)  space, because they are immutable in Java. The space complexity of both the data structures adds up to give O(n) + O(n^2) = O(n^2).

> So in general both performs the same

## Better approach

- to reduce space complexity we can use string builder instead of string
- to reduce time complexity we can ony compare till the mid of the string

### Identify a palindrome using Queue

#### Description

Given an input string of unknown length, write a program to check whether the string is a palindrome or not using a queue data structure. If the string comes out to be a palindrome, then print “ The given input is a palindrome.”  else print “ The given input is not a palindrome.” . Your program should take the following as input from the user: 

The string to be checked for palindrome.

```java
  import java.util.*;
  class Source {

   public void checkPalindrome(String input) {
    char[] stringArray = input.toCharArray();
    Queue<String> plinQueue = new LinkedList<>();
    for( int i=stringArray.length-1; i>= 0;i--){
        plinQueue.add(""+stringArray[i]);
    }
    String reversedString="";
    while(!plinQueue.isEmpty()){
       reversedString = reversedString + plinQueue.remove();
    }
    if(reversedString.equals(input)){
        System.out.println("The given input is a palindrome.");
    }else{
        System.out.println("The given input is not a palindrome.");
    }
   }
   public static void main(String[] args) {
    Source obj = new Source();
    Scanner in = new Scanner(System.in);
    String inputString = in .nextLine();
    obj.checkPalindrome(inputString);

   }
  }

  
```
