# Problem Statement

Given two strings `s` and `t`, return `true` if `t` is an anagram of `s`, and `false` otherwise.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

## Examples

**Example 1:**

- **Input:** `s = "anagram"`, `t = "nagaram"`
- **Output:** `true`

**Example 2:**

- **Input:** `s = "rat"`, `t = "car"`
- **Output:** `false`

## Constraints

- `1 <= s.length, t.length <= 5 * 10^4`
- `s` and `t` consist of lowercase English letters.

# Brute Force Approach

We convert both strings to character arrays and sort them. Then, we compare the sorted arrays to determine if they are equal.

**Time Complexity:** O(n log n) and **Space Complexity:** O(n)

## Solution Code

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) {
            return false;
        }
        char[] sArray = s.toCharArray();
        char[] tArray = t.toCharArray();
        Arrays.sort(sArray);
        Arrays.sort(tArray);
        return Arrays.equals(sArray, tArray);
    }
}
```

# Optimal Approach

Use a frequency count to check if both strings have the same characters with identical counts. 

**Time Complexity:** O(n) and **Space Complexity:** O(1)

## Solution Code

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) {
            return false;
        }

        int[] arr = new int[26];

        for (int i = 0; i < s.length(); i++) {
            arr[s.charAt(i) - 'a']++;
            arr[t.charAt(i) - 'a']--;
        }

        for (int i = 0; i < arr.length; i++) {
            if (arr[i] != 0) {
                return false;
            }
        }
        return true;
    }
}

In case of unicode characters, we can use HashMap. 
