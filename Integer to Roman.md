# [Problem Statement](https://leetcode.com/problems/integer-to-roman/)

Seven different symbols represent Roman numerals with the following values:

| Symbol | Value |
|--------|-------|
| I      | 1     |
| V      | 5     |
| X      | 10    |
| L      | 50    |
| C      | 100   |
| D      | 500   |
| M      | 1000  |

Roman numerals are formed by appending the conversions of decimal place values from highest to lowest. Converting a decimal place value into a Roman numeral has the following rules:

1. **Non-Subtractive Form:** If the value does not start with 4 or 9, select the symbol of the maximal value that can be subtracted from the input, append that symbol to the result, subtract its value, and convert the remainder to a Roman numeral.

2. **Subtractive Form:** If the value starts with 4 or 9, use the subtractive form representing one symbol subtracted from the following symbol, for example:
   - 4 is represented as `IV` (1 less than 5).
   - 9 is represented as `IX` (1 less than 10).

   Only the following subtractive forms are used:
   - 4 (IV)
   - 9 (IX)
   - 40 (XL)
   - 90 (XC)
   - 400 (CD)
   - 900 (CM)

3. **Repetition Rule:** Only powers of 10 (I, X, C, M) can be appended consecutively at most 3 times to represent multiples of 10. Symbols like 5 (V), 50 (L), or 500 (D) cannot be appended multiple times. If a symbol needs to be repeated 4 times, use the subtractive form instead.

### Problem

Given an integer, convert it to a Roman numeral.

### Examples

#### Example 1:

- **Input:** `num = 3749`
- **Output:** `"MMMDCCXLIX"`
- **Explanation:** 
  - 3000 = `MMM` as 1000 (M) + 1000 (M) + 1000 (M)
  - 700 = `DCC` as 500 (D) + 100 (C) + 100 (C)
  - 40 = `XL` as 10 (X) less than 50 (L)
  - 9 = `IX` as 1 (I) less than 10 (X)

  Note: 49 is not 1 (I) less than 50 (L) because the conversion is based on decimal places.

#### Example 2:

- **Input:** `num = 58`
- **Output:** `"LVIII"`
- **Explanation:** 
  - 50 = `L`
  - 8 = `VIII`

#### Example 3:

- **Input:** `num = 1994`
- **Output:** `"MCMXCIV"`
- **Explanation:**
  - 1000 = `M`
  - 900 = `CM`
  - 90 = `XC`
  - 4 = `IV`

### Constraints:

- `1 <= num <= 3999`

## Approach

To solve this problem:

1. **Create Arrays for Values and Symbols:** Make two arrays, one for values and another for corresponding Roman numeral symbols. The arrays are ordered from the highest value to the lowest, including all combinations necessary for subtractive forms.

2. **Iterate Through Values:** Initialize a pointer to traverse through the arrays. Start with the highest value, and while the number is greater than 0:
   - If the current number is greater than or equal to the current value in the array, append the corresponding symbol to the result string and subtract that value from the number.
   - If not, move to the next value in the array.

3. **Return Result:** Continue until the number is reduced to 0. The result string will contain the Roman numeral representation of the input number.

### Time Complexity

- **Time Complexity:** O(1), because the number of operations does not depend on the size of the input number. The number is always between 1 and 3999, so the loop will run a fixed number of times.
- **Space Complexity:** O(1), because the amount of space used by variables is constant.

## Solution Code

```java
class Solution {
    public String intToRoman(int num) {
        int[] value = {1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};
        String[] symbol = {"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};

        int i = 0;      
        StringBuilder sb = new StringBuilder();

        while(num > 0){
            if(num >= value[i]){
                num -= value[i];
                sb.append(symbol[i]);
            } else {
                i++;
            }
        }

        return sb.toString();
    }
}
