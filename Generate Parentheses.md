# [Problem Statement](https://leetcode.com/problems/generate-parentheses/)

Given `n` pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

## Example 1

**Input:** n = 3

**Output:** 
["((()))","(()())","(())()","()(())","()()()"]

## Example 2

**Input:** n = 1

**Output:** ["()"]


## Constraints

- `1 <= n <= 8`

## Optimal Approach

To solve this problem, we use **backtracking**. The idea is to build the string of parentheses step by step while keeping track of the number of open and close parentheses used so far. We ensure that at any point, we do not add more closing parentheses than opening ones.

### Steps:

1. **Base Case:** If the number of open and close parentheses used is equal to `n`, a valid combination is formed, and we add it to the result list.
2. **Recursive Cases:** 
   - If the number of open parentheses used is less than `n`, add an open parenthesis `'('` and make a recursive call.
   - If the number of close parentheses is less than the number of open parentheses used, add a closing parenthesis `')'` and make a recursive call.
   
By following these rules, we ensure all combinations are well-formed and complete.

### Time Complexity

- The time complexity is `O(4^n / sqrt(n))`. This is derived from the Catalan number, which represents the number of valid parentheses combinations for a given `n`.
  
### Space Complexity

- The space complexity is `O(n)` for the recursion stack.

```java
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> list = new ArrayList<>();
        generate(0, 0, n, "", list);
        return list;
    }
    
    public void generate(int open, int close, int n, String s, List<String> list) {
        // Base Case: When the number of open and close parentheses used is equal to n
        if (open == n && close == n) {
            list.add(s);
            return;
        }

        // If the number of open parentheses used is less than n, add an open parenthesis
        if (open < n) {
            generate(open + 1, close, n, s + "(", list);
        }
        
        // If the number of close parentheses is less than open, add a close parenthesis
        if (close < open) {
            generate(open, close + 1, n, s + ")", list);
        }
    }
}
```
