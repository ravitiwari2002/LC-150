# [Problem Statement](https://leetcode.com/problems/binary-search)

Given an array of integers `nums` which is sorted in ascending order, and an integer `target`, write a function to search for `target` in `nums`. If `target` exists, return its index. Otherwise, return `-1`.

You must write an algorithm with `O(log n)` runtime complexity.

## Example 1:

**Input:** nums = [-1,0,3,5,9,12], target = 9

**Output:** 4

**Explanation:** 9 exists in `nums` and its index is `4`.

## Example 2:

**Input:** nums = [-1,0,3,5,9,12], target = 2

**Output:** -1

**Explanation:** 2 does not exist in `nums`, so return `-1`.

## Constraints:

- `1 <= nums.length <= 10^4`
- `-10^4 < nums[i], target < 10^4`
- All the integers in `nums` are unique.
- `nums` is sorted in ascending order.

## Optimal Approach

To solve this problem efficiently with `O(log n)` runtime complexity, we should use **Binary Search**. Binary Search is an algorithm that works on sorted arrays by repeatedly dividing the search interval in half. If the value of the `target` is less than the value in the middle of the interval, the algorithm narrows the interval to the lower half. Otherwise, it narrows it to the upper half. The search continues until the value is found or the interval is empty.
We can also use recursive approach instead of iterative however recurisve approach will use more space as it uses stack. 

### Steps:

1. Initialize two pointers: `left` at the start of the array and `right` at the end.
2. While `left` is less than or equal to `right`:
   - Calculate the `mid` index as `left + (right - left) / 2` to avoid overflow.
   - If `nums[mid]` is equal to `target`, return `mid`.
   - If `nums[mid]` is greater than `target`, adjust `right` to `mid - 1` to search in the left half.
   - If `nums[mid]` is less than `target`, adjust `left` to `mid + 1` to search in the right half.
3. If the `target` is not found, return `-1`.

### Time Complexity

- The time complexity of the binary search algorithm is `O(log n)` because it splits the search space in half with each iteration.

### Space Complexity

- The space complexity is `O(1)` since it uses only a few additional variables.

### Solution Code

```java
class Solution {
    public int search(int[] nums, int target) {
        int left = 0, right = nums.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2; // Calculate mid to avoid overflow

            if (nums[mid] == target) {
                return mid; // Target found
            } else if (nums[mid] < target) {
                left = mid + 1; // Search in the right half
            } else {
                right = mid - 1; // Search in the left half
            }
        }

        return -1; // Target not found
    }
}
```


