## [Problem Statement](https://leetcode.com/problems/roman-to-integer/description/)

Roman numerals are represented by seven different symbols:

| Symbol | Value |
| ------ | ----- |
| I      | 1     |
| V      | 5     |
| X      | 10    |
| L      | 50    |
| C      | 100   |
| D      | 500   |
| M      | 1000  |

For example, 2 is written as `II` in Roman numerals, just two ones added together. 12 is written as `XII`, which is simply `X` + `II`. The number 27 is written as `XXVII`, which is `XX` + `V` + `II`.

Roman numerals are usually written from largest to smallest from left to right. However, the numeral for four is not `IIII`. Instead, the number four is written as `IV`. The same principle applies to the number nine, which is written as `IX`. There are six instances where subtraction is used:

- `I` can be placed before `V` (5) and `X` (10) to make 4 and 9.
- `X` can be placed before `L` (50) and `C` (100) to make 40 and 90.
- `C` can be placed before `D` (500) and `M` (1000) to make 400 and 900.

Given a Roman numeral, convert it to an integer.

### Examples

#### Example 1:
- **Input:** `s = "III"`
- **Output:** `3`
- **Explanation:** `III` = 3.

#### Example 2:
- **Input:** `s = "LVIII"`
- **Output:** `58`
- **Explanation:** `L` = 50, `V` = 5, `III` = 3.

#### Example 3:
- **Input:** `s = "MCMXCIV"`
- **Output:** `1994`
- **Explanation:** `M` = 1000, `CM` = 900, `XC` = 90, `IV` = 4.

### Constraints:
- `1 <= s.length <= 15`
- `s` contains only the characters `('I', 'V', 'X', 'L', 'C', 'D', 'M')`.
- It is guaranteed that `s` is a valid Roman numeral in the range `[1, 3999]`.

  ## Approach

Since in Roman numerals, smaller values can precede larger values to indicate subtraction (like `IV` for 4 or `IX` for 9), we can utilize a map to store the Roman numeral symbols and their corresponding values. We iterate over the string and compare the current character with the next character:
- If the current character represents a smaller value than the next one, subtract it from the total.
- Otherwise, add it to the total.
- Finally, add the value of the last character.

### Time Complexity
- **Time Complexity:** O(n), where `n` is the length of the string.
- **Space Complexity:** O(1), because the space used by the map and the integer total is constant.

## Solution Code

```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    public int romanToInt(String s) {
        Map<Character, Integer> map = new HashMap<>();

        map.put('I', 1);
        map.put('V', 5);
        map.put('X', 10);
        map.put('L', 50);
        map.put('C', 100);
        map.put('D', 500);
        map.put('M', 1000);

        int ans = 0;

        for (int i = 0; i < s.length() - 1; i++) {
            if (map.get(s.charAt(i)) < map.get(s.charAt(i + 1))) {
                ans -= map.get(s.charAt(i));
            } else {
                ans += map.get(s.charAt(i));
            }
        }

        return ans + map.get(s.charAt(s.length() - 1));
    }
}
```
