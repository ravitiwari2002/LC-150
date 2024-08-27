# Problem Statement

Given a string `s`, find the first non-repeating character in it and return its index. If it does not exist, return `-1`.

## Example 1:

**Input:** s = "leetcode"

**Output:** 0


## Example 2:

**Input:** s = "loveleetcode"

**Output:** 2


## Approach

To solve this problem, we can use a `HashMap` to store the frequency of each character in the string. After building the frequency map, we can iterate through the string again to find the first character that appears only once.

### Steps

1. Create a `HashMap` to store the frequency of each character in the string.
2. Iterate through the string to populate the hashmap.
3. Iterate through the string a second time to find the first character with a frequency of 1 in the hashmap.
4. Return the index of the first non-repeating character, or `-1` if no such character exists.

### Time Complexity

- **O(n)**: We traverse the string twice — once to build the frequency map and once to find the first unique character.

### Space Complexity

- **O(1)**: The space complexity is O(1) since the maximum number of unique characters is fixed (26 for lowercase English letters).

### Solution Code

```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    public int firstUniqChar(String s) {
        // Step 1: Create a HashMap to store character frequencies
        Map<Character, Integer> map = new HashMap<>();

        // Step 2: Populate the frequency map
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            map.put(c, map.getOrDefault(c, 0) + 1);
        }

        // Step 3: Find the first unique character
        for (int i = 0; i < s.length(); i++) {
            if (map.get(s.charAt(i)) == 1) {
                return i;
            }
        }

        // Step 4: Return -1 if no unique character is found
        return -1;
    }
}
```




