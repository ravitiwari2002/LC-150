# Problem Statement

Given an array of strings `strs`, group the anagrams together. You can return the answer in any order.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

## Examples

**Example 1:**

- **Input:** `strs = ["eat","tea","tan","ate","nat","bat"]`
- **Output:** `[["bat"],["nat","tan"],["ate","eat","tea"]]`

**Example 2:**

- **Input:** `strs = [""]`
- **Output:** `[[""]]`

**Example 3:**

- **Input:** `strs = ["a"]`
- **Output:** `[["a"]]`

## Constraints

- `1 <= strs.length <= 10^4`
- `0 <= strs[i].length <= 100`
- `strs[i]` consists of lowercase English letters.

# Brute Force Approach

Compare each string with every other string to check if they are anagrams by sorting their characters and grouping them accordingly.

**Time Complexity:** O(n<sup>2</sup> * k log k)  
**Space Complexity:** O(n * k)

## Solution Code

```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        List<List<String>> result = new ArrayList<>();
        boolean[] visited = new boolean[strs.length];

        for (int i = 0; i < strs.length; i++) {
            if (!visited[i]) {
                List<String> group = new ArrayList<>();
                group.add(strs[i]);
                visited[i] = true;

                for (int j = i + 1; j < strs.length; j++) {
                    if (!visited[j] && areAnagrams(strs[i], strs[j])) {
                        group.add(strs[j]);
                        visited[j] = true;
                    }
                }
                result.add(group);
            }
        }
        return result;
    }

    private boolean areAnagrams(String s1, String s2) {
        if (s1.length() != s2.length()) {
            return false;
        }
        char[] s1Array = s1.toCharArray();
        char[] s2Array = s2.toCharArray();
        Arrays.sort(s1Array);
        Arrays.sort(s2Array);
        return Arrays.equals(s1Array, s2Array);
    }
}
```
# Optimal Approach

This approach uses a `HashMap` to group anagrams. Each string in the input array is sorted, and this sorted string serves as a key in the map. Anagrams will have the same sorted string, so they will be grouped under the same key.

**Time Complexity:** \(O(n \times k \log k)\), where \(n\) is the number of strings, and \(k\) is the maximum length of a string in `strs`.

**Space Complexity:** \(O(n \times k)\), due to the storage needed for the map and the groups of anagrams.

## Solution Code

```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        HashMap<String, List<String>> map = new HashMap<>();

        for(int i = 0; i < strs.length; i++){
            char[] tmp = strs[i].toCharArray();
            Arrays.sort(tmp);
            String s = String.valueOf(tmp);

            if(!map.containsKey(s)){
                map.put(s, new ArrayList<String>());
            }            
            map.get(s).add(strs[i]);
        }
        return new ArrayList<>(map.values());
    }
}
```
