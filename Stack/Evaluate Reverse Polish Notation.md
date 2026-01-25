Evaluate Reverse Polish Notation
Solved 
Medium
Company Tags
Hints
You are given an array of strings tokens that represents a valid arithmetic expression in Reverse Polish Notation.

Return the integer that represents the evaluation of the expression.

The operands may be integers or the results of other operations.
The operators include '+', '-', '*', and '/'.
Assume that division between integers always truncates toward zero.
Example 1:

Input: tokens = ["1","2","+","3","*","4","-"]

Output: 5

Explanation: ((1 + 2) * 3) - 4 = 5
Constraints:

1 <= tokens.length <= 1000.
tokens[i] is "+", "-", "*", or "/", or a string representing an integer in the range [-100, 100].
-------------------------------------------------------------------------------------------------

        class Solution {
            public int evalRPN(String[] tokens) {
                Stack<Integer> stack = new Stack<>();
                for(String t : tokens){
                    if(t.equals("+")){
                        stack.push(stack.pop() + stack.pop());
                    }else if(t.equals("*")){
                        stack.push(stack.pop() * stack.pop());
                    }else if(t.equals("-")){
                        int a = stack.pop();
                        int b = stack.pop();
                        stack.push(b - a);
                    }else if(t.equals("/")){
                        int a = stack.pop();
                        int b = stack.pop();
                        stack.push(b / a);
                    }else{
                        stack.push(Integer.parseInt(t));
                    }
                }
                return stack.pop();
            }
        }
-----------------------------------------------------------------------------------

Time & Space Complexity
Time complexity: 
O(n)
Space complexity: 
O(n)

----------------------------------------
Note : 
only for multiply and addition we can write in one line push, as division and subtraction needs two variable to perform operation to avoid negative value.
