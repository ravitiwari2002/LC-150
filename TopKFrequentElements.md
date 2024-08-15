# Problem Statement

Given an integer array `nums` and an integer `k`, return the `k` most frequent elements. You may return the answer in any order.

## Examples

**Example 1:**

- **Input:** `nums = [1,1,1,2,2,3], k = 2`
- **Output:** `[1,2]`

**Example 2:**

- **Input:** `nums = [1], k = 1`
- **Output:** `[1]`

## Brute Force Approach

Count the frequency of each element using nested loops, sort the elements by their frequency, and then select the top `k` elements from the sorted list.

**Time Complexity:** O(n<sup>2</sup>) and **Space Complexity:** O(n)

## Solution Code

```java
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        List<int[]> frequencyList = new ArrayList<>();
       
        for (int i = 0; i < nums.length; i++) {
            boolean found = false;
            for (int[] pair : frequencyList) {
                if (pair[0] == nums[i]) {
                    pair[1]++;
                    found = true;
                    break;
                }
            }
            if (!found) {
                frequencyList.add(new int[]{nums[i], 1});
            }
        }

        Collections.sort(frequencyList, (a, b) -> b[1] - a[1]);

        int[] result = new int[k];
        for (int i = 0; i < k; i++) {
            result[i] = frequencyList.get(i)[0];
        }

        return result;
    }
}
```
