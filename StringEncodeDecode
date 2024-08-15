# Problem Statement

Design an algorithm to encode a list of strings to a single string. The encoded string is then decoded back to the original list of strings.

Please implement `encode` and `decode`.

## Examples

**Example 1:**

- **Input:** `["neet","code","love","you"]`
- **Output:** `["neet","code","love","you"]`

**Example 2:**

- **Input:** `["we","say",":","yes"]`
- **Output:** `["we","say",":","yes"]`

## Solution

**Encoding**: We encode by putting the length of each string before the string, separated by `#`. For example, "hello" would be encoded as `5#hello`.

**Decoding**: To decode, we parse the encoded string to extract the lengths and substrings accordingly.

**Time Complexity:** O(n), where `n` is the total number of characters across all strings.

**Space Complexity:** O(n), where `n` is the total number of characters in the encoded string.

## Solution Code

```java
class Solution {

    public String encode(List<String> strs) {
        StringBuilder sb = new StringBuilder();

        for (String str : strs) {
            sb.append(str.length()).append("#").append(str);
        }
        
        return sb.toString();
    }

    public List<String> decode(String str) {
        List<String> list = new ArrayList<>();
        int i = 0;

        while (i < str.length()) {
            StringBuilder lengthStr = new StringBuilder();
            while (str.charAt(i) != '#') {
                lengthStr.append(str.charAt(i));
                i++;
            }

            int len = Integer.parseInt(lengthStr.toString());
            i++;

            list.add(str.substring(i, i + len));
            i = i + len;
        }

        return list;
    }
}
```
