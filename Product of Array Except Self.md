# Problem Statement

Given an integer array `nums`, return an array `answer` such that `answer[i]` is equal to the product of all the elements of `nums` except `nums[i]`. You must write an algorithm that runs in O(n) time and without using the division operation.

## Examples

**Example 1:**

- **Input:** `nums = [1,2,3,4]`
- **Output:** `[24,12,8,6]`

**Example 2:**

- **Input:** `nums = [-1,1,0,-3,3]`
- **Output:** `[0,0,9,0,0]`

## Approach 1

The approach involves counting zeros in the array and calculating the product of non-zero elements to handle different cases:

1. **Count Zeros and Compute Product:**
   - Traverse the array to count zeros and compute the product of non-zero elements.
   - If there are more than one zero, the result will be an array of zeros.

2. **Handle Different Cases:**
   - If exactly one zero, set all elements to zero except the position of the zero, which gets the total product of non-zero elements.
   - If no zeros, use division to compute each element of the result.

**Time Complexity:** O(n)  
**Space Complexity:** O(1) (excluding the output array)

## Solution Code

```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int zeroCount = 0;
        int product = 1;
        int totalZeroIndex = -1;
       
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == 0) {
                zeroCount++;
                if (zeroCount > 1) {
                    return new int[nums.length]; 
                }
                totalZeroIndex = i;
            } else {
                product *= nums[i];
            }
        }
       
        if (zeroCount == 1) {
            int[] result = new int[nums.length];
            for (int i = 0; i < nums.length; i++) {
                if (i != totalZeroIndex) {
                    result[i] = 0;
                } else {
                    result[i] = product;
                }
            }
            return result;
        }
        
        int[] result = new int[nums.length];
        for (int i = 0; i < nums.length; i++) {
            result[i] = product / nums[i];
        }
        return result;
    }
}
```
