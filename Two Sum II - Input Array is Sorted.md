# [Problem Statement](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

Given a 1-indexed array of integers `numbers` that is already sorted in non-decreasing order, find two numbers such that they add up to a specific target number. Let these two numbers be `numbers[index1]` and `numbers[index2]` where `1 <= index1 < index2 <= numbers.length`.

Return the indices of the two numbers, `index1` and `index2`, added by one as an integer array `[index1, index2]` of length 2.

The tests are generated such that there is exactly one solution. You may not use the same element twice.

Your solution must use only constant extra space.

### Examples

#### Example 1:

- **Input:** `numbers = [2,7,11,15], target = 9`
- **Output:** `[1,2]`
- **Explanation:** The sum of 2 and 7 is 9. Therefore, `index1 = 1`, `index2 = 2`. We return `[1, 2]`.

#### Example 2:

- **Input:** `numbers = [2,3,4], target = 6`
- **Output:** `[1,3]`
- **Explanation:** The sum of 2 and 4 is 6. Therefore, `index1 = 1`, `index2 = 3`. We return `[1, 3]`.

#### Example 3:

- **Input:** `numbers = [-1,0], target = -1`
- **Output:** `[1,2]`
- **Explanation:** The sum of -1 and 0 is -1. Therefore, `index1 = 1`, `index2 = 2`. We return `[1, 2]`.

### Constraints

- `2 <= numbers.length <= 3 * 10^4`
- `-1000 <= numbers[i] <= 1000`
- `numbers` is sorted in non-decreasing order.
- `-1000 <= target <= 1000`
- The tests are generated such that there is exactly one solution.

### Optimal Approach

Since the array is sorted, we can use the two-pointer technique to find the two numbers that sum up to the target. The idea is to initialize two pointers: one at the beginning (`left`) and one at the end (`right`) of the array. 

- If the sum of the numbers at these two pointers is less than the target, we move the left pointer to the right (`left++`) to increase the sum.
- If the sum is greater than the target, we move the right pointer to the left (`right--`) to decrease the sum.
- If the sum is equal to the target, we return the indices of the two numbers (adding 1 to each to convert from 0-based to 1-based indexing).

#### Time Complexity: 
- O(n), where n is the length of the array. We traverse the array once with the two pointers.

#### Space Complexity: 
- O(1), as we are using only a constant amount of extra space.

```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int index1 = 0;
        int index2 = numbers.length - 1;

        while (index1 < index2) {
            if (numbers[index1] + numbers[index2] == target) {
                return new int[] {index1 + 1, index2 + 1}; // Return the 1-based indices
            } else if (numbers[index1] + numbers[index2] > target) {
                index2--; // Move the right pointer to the left
            } else {
                index1++; // Move the left pointer to the right
            }
        }
        return new int[0]; // In case there is no solution, though per constraints, there will be one
    }
}
```
