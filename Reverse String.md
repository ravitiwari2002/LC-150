# [Problem Statement](https://leetcode.com/problems/reverse-string/description/)

Write a function that reverses a string. The input string is given as an array of characters `s`.

You must do this by modifying the input array in-place with O(1) extra memory.

## Examples

### Example 1
- **Input**: `s = ["h","e","l","l","o"]`
- **Output**: `["o","l","l","e","h"]`

### Example 2
- **Input**: `s = ["H","a","n","n","a","h"]`
- **Output**: `["h","a","n","n","a","H"]`

## Constraints
- `1 <= s.length <= 10^5`
- `s[i]` is a printable ASCII character.

## Approach: We use two pointers approach to swap characters of string.

**Time Complexity:** O(n)

**Space Complexity:** O(1)

### Solution

```java
public class Solution {
    public void reverseString(char[] s) {
        int left = 0;
        int right = s.length - 1;
        while (left < right) {
            char temp = s[left];
            s[left] = s[right];
            s[right] = temp;
            left++;
            right--;
        }
    }
}

```
