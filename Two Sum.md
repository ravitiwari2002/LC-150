# [Problem Statement](https://leetcode.com/problems/two-sum/)

Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

You may assume that each input would have exactly one solution, and you may not use the same element twice. You can return the answer in any order.

## Examples

**Example 1:**

- **Input:** `nums = [2,7,11,15]`, `target = 9`
- **Output:** `[0,1]`
- **Explanation:** Because `nums[0] + nums[1] == 9`, we return `[0, 1]`.

**Example 2:**

- **Input:** `nums = [3,2,4]`, `target = 6`
- **Output:** `[1,2]`

**Example 3:**

- **Input:** `nums = [3,3]`, `target = 6`
- **Output:** `[0,1]`

## Constraints

- `2 <= nums.length <= 10^4`
- `-10^9 <= nums[i] <= 10^9`
- `-10^9 <= target <= 10^9`
- Only one valid answer exists.

# Brute Force Approach

We use nested for loops to iterate through each pair of elements in the array and check if their sum equals the target. If a matching pair is found, return their indices.

**Time Complexity:** O(n<sup>2</sup>)  
**Space Complexity:** O(1)

## Solution Code

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
       for(int i = 0; i < nums.length; i++){
            for(int j = i+1; j < nums.length; j++){
                if(nums[i] + nums[j] == target){
                    return new int[] {i, j};
                }
            }
       }
       return new int[]{};
    }
}
```

# Optimal Approach

We use a `HashMap` to store the elements of the array as keys and their indices as values. As we iterate over the array, we calculate the difference between the target and the current element. If this difference is found in the `HashMap`, it means we have found the two numbers that add up to the target. We return their indices. If the difference is not in the `HashMap`, we add the current element and its index to the `HashMap`.

**Time Complexity:** O(n)  
**Space Complexity:** O(n)

## Solution Code

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();

        for (int i = 0; i < nums.length; i++) {
            int diff = target - nums[i];

            if (map.containsKey(diff)) {
                return new int[] {i, map.get(diff)};
            } else {
                map.put(nums[i], i);
            }
        }
        return new int[]{};
    }
}
```
