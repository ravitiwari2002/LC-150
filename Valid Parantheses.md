## [Problem Statement](https://leetcode.com/problems/valid-parentheses/description/)

Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:
- Open brackets must be closed by the same type of brackets.
- Open brackets must be closed in the correct order.
- Every close bracket has a corresponding open bracket of the same type.

### Examples

**Example 1:**
- **Input:** `s = "()"`  
- **Output:** `true`

**Example 2:**
- **Input:** `s = "()[]{}"`  
- **Output:** `true`

**Example 3:**
- **Input:** `s = "(]"`  
- **Output:** `false`

### Constraints

- `1 <= s.length <= 10^4`
- `s` consists of parentheses only `'()[]{}'`.

## Brute Force Approach

Using the String method, we iteratively replace all instances of `"()"`, `"{}"`, and `"[]"` with an empty string `""`. We continue this process until no more replacements can be made, and then we check if the remaining string is empty.

### Time Complexity: **O(n<sup>2</sup>)** and Space Complexity: **O(n)**. Because String Manipulation in Java is not in-place.

```java
class Solution {
    public boolean isValid(String s) {
        while (true) {
            if (s.contains("()")) {
                s = s.replace("()", "");
            } else if (s.contains("{}")) {
                s = s.replace("{}", "");
            } else if (s.contains("[]")) {
                s = s.replace("[]", "");
            } else {
                return s.isEmpty();
            }
        }
    }
}
```
## Optimal Approach

We use a stack to keep track of opening brackets as we traverse the string. For each character in the string:
- If it is an opening bracket (`(`, `{`, `[`), we push it onto the stack.
- If it is a closing bracket (`)`, `}`, `]`), we check the stack:
  - If the stack is empty, we return `false` as there is no matching opening bracket.
  - If the stack is not empty, we peek at the top element:
    - If it matches the corresponding opening bracket, we pop it from the stack.
    - If it does not match, we return `false`.
- After processing all characters, we check if the stack is empty. If it is, the string is valid; otherwise, it is not.

### Time Complexity: **O(n)** and Space Complexity: **O(n)**

```java
class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();

        for (int i = 0; i < s.length(); i++) {
            
            if (s.charAt(i) == '(' || s.charAt(i) == '{' || s.charAt(i) == '[') {
                stack.push(s.charAt(i));
            } else {
                if (stack.isEmpty()) {
                    return false;
                }
                
                if ((s.charAt(i) == ')' && stack.peek() == '(') || 
                    (s.charAt(i) == '}' && stack.peek() == '{') || 
                    (s.charAt(i) == ']' && stack.peek() == '[')) {
                    stack.pop();
                } else {
                    return false;
                }
            }
        }
        return stack.isEmpty();
    }
}
```
