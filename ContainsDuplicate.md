# Brute Force Approach to Detect Duplicates

This solution uses a brute force approach to determine if an array contains any duplicates by comparing each element with every other element using nested loops.

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
