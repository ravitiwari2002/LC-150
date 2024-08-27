# [Problem Statement](https://leetcode.com/problems/evaluate-reverse-polish-notation/)

You are given an array of strings `tokens` that represents an arithmetic expression in Reverse Polish Notation.

Evaluate the expression and return an integer that represents the value of the expression.

## Notes:

- The valid operators are '+', '-', '*', and '/'.
- Each operand may be an integer or another expression.
- The division between two integers always truncates toward zero.
- There will not be any division by zero.
- The input represents a valid arithmetic expression in reverse polish notation.
- The answer and all the intermediate calculations can be represented in a 32-bit integer.

## Examples

### Example 1

**Input:**  
`tokens = ["2","1","+","3","*"]`

**Output:**  
`9`

**Explanation:**  
`((2 + 1) * 3) = 9`

### Example 2

**Input:**  
`tokens = ["4","13","5","/","+"]`

**Output:**  
`6`

**Explanation:**  
`(4 + (13 / 5)) = 6`

### Example 3

**Input:**  
`tokens = ["10","6","9","3","+","-11","*","/","*","17","+","5","+"]`

**Output:**  
`22`

### Optimal Approach

To solve this problem, we use a **stack** to evaluate the expression in Reverse Polish Notation (RPN).

## Approach:

1. **Initialize a stack** to store integers.
2. **Iterate over each token** in the input array `tokens`:
   - If the token is an **operator** (`+`, `-`, `*`, `/`), pop the **top two elements** from the stack.
   - Perform the operation between these two elements and push the **result back onto the stack**.
   - If the token is a **number**, convert it to an integer and push it onto the stack.
3. **Continue this process** until all tokens are processed.
4. The **final result** of the expression will be the only element left in the stack.

## Time Complexity:
- **O(n)**, where `n` is the number of tokens. We iterate through the tokens array once, performing constant-time operations (push, pop, and arithmetic operations).

## Space Complexity:
- **O(n)**, for the stack used to store numbers. In the worst case, if all tokens are numbers, we need to store all of them in the stack.

```java
class Solution {
    public int evalRPN(String[] tokens) {
        Stack<Integer> stack = new Stack<>();

        for(int i = 0; i < tokens.length; i++){
            if(tokens[i].equals("+")){
                stack.push(stack.pop() + stack.pop());
            }
            else if(tokens[i].equals("*")){
                stack.push(stack.pop() * stack.pop());
            }
            else if(tokens[i].equals("-")){
                int top = stack.pop();
                int bottom = stack.pop();
                stack.push(bottom - top);  // Correct order for subtraction
            }
            else if(tokens[i].equals("/")){
                int top = stack.pop();
                int bottom = stack.pop();
                stack.push(bottom / top);  // Correct order for division
            }
            else {
                stack.push(Integer.parseInt(tokens[i]));
            }
        }
        return stack.peek();  // The result is the top of the stack
    }
}
```

