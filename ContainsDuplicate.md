# Problem Statement

Given an integer array `nums`, return `true` if any value appears at least twice in the array, and return `false` if every element is distinct.

## Examples

**Example 1:**

- **Input:** `nums = [1,2,3,1]`
- **Output:** `true`

**Example 2:**

- **Input:** `nums = [1,2,3,4]`
- **Output:** `false`

**Example 3:**

- **Input:** `nums = [1,1,1,3,3,4,3,2,4,2]`
- **Output:** `true`

# Brute Force Approach 

This solution uses a brute force approach to determine if an array contains any duplicates by comparing each element with every other element using nested loops. 
**Time Complexity:** O(n<sup>2</sup>) 
**Space Complexity:** O(1)

## Solution Code

```java
class Solution {
    public boolean containsDuplicate(int[] nums) {        
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] == nums[j]) {
                    return true;
                }
            }
        }
        return false;
    }
}
