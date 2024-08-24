# Problem Statement

Given an integer array `nums`, return all the unique triplets `[nums[i], nums[j], nums[k]]` such that:
- `i != j`, `i != k`, and `j != k`
- `nums[i] + nums[j] + nums[k] == 0`

The solution set must not contain duplicate triplets.

### Examples

**Example 1:**

Input: `nums = [-1,0,1,2,-1,-4]`  
Output: `[[-1,-1,2],[-1,0,1]]`  
Explanation: 
- `nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0`
- `nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0`
- `nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0`
- The distinct triplets are `[-1,-1,2]` and `[-1,0,1]`

**Example 2:**

Input: `nums = [0,1,1]`  
Output: `[]`  
Explanation: The only possible triplet does not sum up to 0.

**Example 3:**

Input: `nums = [0,0,0]`  
Output: `[[0,0,0]]`  
Explanation: The only possible triplet sums up to 0.

### Constraints

- `3 <= nums.length <= 3000`
- `-10^5 <= nums[i] <= 10^5`

## Approach

1. **Sorting:** First, sort the input array `nums`. Sorting helps us efficiently use the two-pointer technique to find the triplets.

2. **Iteration:** Iterate over the array up to the second last element since we are looking for triplets (`i < nums.length - 2`).

3. **Two Pointers Technique:**
   - For each element `nums[i]` in the sorted array:
     - Set two pointers: `left` at `i + 1` and `right` at the last index (`nums.length - 1`).
     - Check the sum of the current element `nums[i]` and the elements at the two pointers (`nums[left]` and `nums[right]`).
     - If the sum is zero, add the triplet `[nums[i], nums[left], nums[right]]` to the result set and move both pointers (`left++` and `right--`).
     - If the sum is less than zero, increment the `left` pointer to increase the sum.
     - If the sum is greater than zero, decrement the `right` pointer to decrease the sum.

4. **Avoid Duplicates:** Use a `Set` to store the triplets to avoid duplicates automatically.

5. **Result:** Convert the `Set` to a `List` and return it as the output.

### Time Complexity

- **Sorting:** O(n log n)
- **Two Pointers Search:** O(n^2)

Overall, the time complexity is **O(n^2)**, where `n` is the number of elements in the input array.

### Space Complexity

- **Auxiliary Space:** O(n) for the result set.

Overall, the space complexity is **O(n)**.

### Java Code

```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);

        Set<List<Integer>> result = new HashSet<>();

        for (int i = 0; i < nums.length - 2; i++) {
            int tmp = nums[i];
            int left = i + 1;
            int right = nums.length - 1;

            while (left < right) {
                if (tmp + nums[right] + nums[left] == 0) {
                    result.add(Arrays.asList(tmp, nums[right], nums[left]));
                    left++;
                    right--;
                } else if (tmp + nums[right] + nums[left] < 0) {
                    left++;
                } else {
                    right--;
                }
            }
        }
        return new ArrayList<>(result);
    }
}
```
