# [Problem Statement](https://leetcode.com/problems/valid-palindrome/description/)

A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string `s`, return `true` if it is a palindrome, or `false` otherwise.

## Examples

**Example 1:**

- Input: `s = "A man, a plan, a canal: Panama"`
- Output: `true`
- Explanation: `"amanaplanacanalpanama"` is a palindrome.

**Example 2:**

- Input: `s = "race a car"`
- Output: `false`
- Explanation: `"raceacar"` is not a palindrome.

**Example 3:**

- Input: `s = " "`
- Output: `true`
- Explanation: `s` is an empty string `""` after removing non-alphanumeric characters. Since an empty string reads the same forward and backward, it is a palindrome.

## Constraints

- `1 <= s.length <= 2 * 10^5`
- `s` consists only of printable ASCII characters.

## Approach

1. Remove all non-alphanumeric characters from the string and convert it to lowercase. Use two pointers to compare characters from the beginning and end of the string, moving towards the center.

**Time Complexity:** O(n) and **Space Complexity:** O(n)

## Solution Code

```java
class Solution {
    public boolean isPalindrome(String s) {
        StringBuilder updated = new StringBuilder();
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            if (Character.isDigit(c) || Character.isLetter(c)) {
                updated.append(Character.toLowerCase(c));
            }
        }

        int pointer1 = 0;
        int pointer2 = updated.length() - 1;

        while (pointer1 <= pointer2) {
            if (updated.charAt(pointer1) != updated.charAt(pointer2)) {
                return false;
            }
            pointer1++;
            pointer2--;
        }
        return true;
    }
}
```
