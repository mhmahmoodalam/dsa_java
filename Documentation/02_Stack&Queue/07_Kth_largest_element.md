# find the kth largest element in a stack

Sorting refers to arranging a sequence of data systematically based on specific criteria. One of the benefits of sorting is that it makes selection easier. For example, if you need to find the kth largest element in a list of numbers, then you can reach that element in constant time if the list is arranged in either descending or ascending order. Stacks and queues are two data structures that are used frequently for storing data. Hence, you will encounter situations where you need to sort elements using these data structures. 

The algorithm to sort the elements of a stack using another stack data structure has O(n^2) time and O(n) space complexity

## Pseudocode

- create a new stack; call it temp;
- while input stack is not empty
    - pop top value from input stack & store it in variable 'value'
    - while 'temp stack is not empty and value < top of the temp stack
        - pop top value from temp stack & push it to the input stack
    - push the value to temp stack
- return temp stack containing all elements in descending sorted order

``` java

import java.util.*;

public class Source {
  // This function returns the sorted stack
   public static Stack < Integer > sortStack(Stack < Integer > stack) {
       
        Stack<Integer> tempStack = new Stack<>();
        while( !stack.isEmpty()){
            int top= stack.pop();
            if(tempStack.isEmpty()){
               tempStack.push(top);
           }else {
               while( !tempStack.isEmpty() && top < tempStack.peek()){
                     stack.push(tempStack.pop());
                }
                tempStack.push(top);
           }
        } 
        return tempStack;
   
   }

   public static void findKthLargestNum(Stack <Integer> sortedStack, int k) {
     int count =k;
     while(!sortedStack.isEmpty() && count > 1 ){
         sortedStack.pop();
         count --;
     }
     System.out.println(sortedStack.peek());
   }


  public static void main(String args[]) {
        Stack < Integer > inputStack = new Stack < Integer > ();
        Scanner in = new Scanner(System.in);
        int n = in .nextInt();
        for (int i = 0; i < n; i++) {
            inputStack.add( in .nextInt());
        }

        if (inputStack.isEmpty()) {
            System.out.println("stack is empty");
            System.exit(0);
        }

        int k = in .nextInt();
        if (k > inputStack.size()) {
            System.out.println("invalid input");
            System.exit(0);
        }

        // This is the temporary stack

        Stack < Integer > temp = sortStack(inputStack);
        //System.out.println(temp);
        findKthLargestNum(temp, k);

    }
}

```
