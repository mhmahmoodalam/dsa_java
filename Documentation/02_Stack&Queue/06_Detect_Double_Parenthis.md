# Detect Duplicate Parentheses

For any programming language structure or for any algebraic expression, it is mandatory to have all parentheses '( )' balanced. You may, for instance, have a balanced algebraic expression that may contain opening and closing parentheses, although there may be instances where these parentheses are duplicated.

 
 For example:

               (((1*2))+5)

Here, 1*2 is enclosed within two pairs of parentheses, whereas just one pair was enough. Your task is to identify the duplicate parentheses in such given balanced algebraic expression.

Finding duplicate parentheses is different from detecting balanced parentheses, but both of them are necessary. Duplicate parentheses lead to wastage of memory and yield a complex representation of any given expression. 


```java
import java.util.*;
class Source {
    public static String findDuplicateParenthesis(String inputString) {
        //write your code here
        boolean dupParenth = false;
        Stack<String> stack= new Stack<>();
        char[] input = inputString.toCharArray();
        int exprCount=0;
        for(int i =0; i<input.length;i++){
            //System.out.println(stack);
            //System.out.println(input[i]);
            if(input[i]!=')'&&input[i]!='}'&&input[i]!=']'){
                stack.push(""+input[i]);
                if(input[i]!='('&&input[i]!='{'&&input[i]!='['){
                    exprCount++;
                }
            }else if(exprCount > 0) {
                while(!matchParenthisClosing(""+input[i],stack.peek())){
                    stack.pop();exprCount--;
                }
                stack.pop();
            }else{
                return "Input string contains duplicate parenthesis";
            }
        }
        return "Input string does not contain duplicate parenthesis";
        
    }

    static boolean matchParenthisClosing(String closing, String toMatch){
        boolean isMacthing=false;
        switch(closing){
            case ")": isMacthing= toMatch.equals("(");break;
             case "}": isMacthing= toMatch.equals("{");break;
              case "]": isMacthing= toMatch.equals("[");break;
        }
        //System.out.println("Macthing :"+closing+" with:"+toMatch+" Result:"+isMacthing);
        return isMacthing;
    }

        public static void main(String[] args){
            Source obj = new Source();
            String inputString = new String();
            Scanner in = new Scanner(System.in);
            inputString = in.nextLine();
            System.out.println(obj.findDuplicateParenthesis(inputString));

        }

    }


```