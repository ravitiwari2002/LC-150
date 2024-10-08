# [Problem Statement](https://leetcode.com/problems/product-of-array-except-self/)

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
## Approach 2

This approach involves creating two arrays to hold the product of elements to the left and right of each element, and then computing the final result by multiplying the corresponding products from both arrays:

1. **Initialize Arrays:**
   - Create `left` and `right` arrays to store the product of elements to the left and right of each index, respectively. Initialize `left[0]` and `right[nums.length - 1]` to 1.

2. **Compute Products:**
   - Populate the `left` array by iterating from left to right.
   - Populate the `right` array by iterating from right to left.

3. **Compute Final Result:**
   - Calculate the result for each index by multiplying the corresponding values from `left` and `right` arrays.

**Time Complexity:** O(n)  
**Space Complexity:** O(n)

## Solution Code

```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int[] left = new int[nums.length];
        left[0] = 1;

        int[] right = new int[nums.length];
        right[nums.length-1] = 1;

        int[] ans = new int[nums.length];

        // Fill left products
        for(int i = 1; i < nums.length; i++){
            left[i] = nums[i-1] * left[i-1];
        }

        // Fill right products
        for(int i = nums.length-2; i >=0 ; i--){
            right[i] = right[i+1] * nums[i+1];
        }

        // Compute final result
        for(int i = 0; i < nums.length; i++){
            ans[i] = left[i]*right[i];
        }

        return ans;
    }
}
```

## Approach 3: Using Output Array for Left and Right Products

We create two passes over the array to calculate the product of all elements to the left and right of each index. 

1. **Compute Left Products in Output Array:**
   - Initialize the output array where `output[i]` will store the product of all elements to the left of `i`.
   - Traverse the array from left to right to populate the `output` array with these products.

2. **Compute Right Products Using a Running Variable:**
   - Traverse the array from right to left using a running variable to keep track of the product of all elements to the right of the current index.
   - Update the `output` array by multiplying it with the running variable to get the final result.

**Time Complexity:** O(n) and **Space Complexity:** O(1) (excluding the output array)

## Solution Code

```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        int[] output = new int[n];
        
        // Step 1: Compute the product of elements to the left of each index
        output[0] = 1;
        for (int i = 1; i < n; i++) {
            output[i] = output[i - 1] * nums[i - 1];
        }

        // Step 2: Compute the product of elements to the right of each index
        int rightProduct = 1;
        for (int i = n - 1; i >= 0; i--) {
            output[i] *= rightProduct;
            rightProduct *= nums[i];
        }

        return output;
    }
}
```
