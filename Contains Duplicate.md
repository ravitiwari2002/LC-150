# [Problem Statement](https://leetcode.com/problems/contains-duplicate/)

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

Compare each element with every other element using nested loops. 

**Time Complexity:** O(n<sup>2</sup>) and **Space Complexity:** O(1)

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
```

# Optimal Approach 

Insert all elements into a `HashSet`. If an element already exists in the `HashSet`, the add operation will return `false`, indicating that the element is a duplicate. 

**Time Complexity:** O(n) and **Space Complexity:** O(n)

## Solution Code

```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashSet<Integer> set = new HashSet<>();
        for(int i = 0; i < nums.length; i++){
            if(!set.add(nums[i])){
                return true;
            }
            else{
                set.add(nums[i]);
            }
        }
        return false;
    }
}
```
