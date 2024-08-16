## Problem Statement

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

### Time Complexity: 
- The time complexity is **O(n<sup>2</sup>)** and Space Complexity: - The space complexity is **O(n)**. Because String Manipulation in Java is not in-place.

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
