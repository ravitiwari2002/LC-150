# [Problem Statement](https://leetcode.com/problems/top-k-frequent-elements/)

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

## Optimal Approach

Iterate over the array and put keys in a `HashMap`. If a key is already in the `HashMap`, increment its value by 1. Then add all entries from the `HashMap` to a max heap (priority queue) and return the top `k` elements from the max heap.

**Time Complexity:** O(n log n)  
**Space Complexity:** O(n)

## Solution Code

```java
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        Map<Integer, Integer> map = new HashMap<>();
        int[] ans = new int[k];

        for (int num : nums) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }

        PriorityQueue<Map.Entry<Integer, Integer>> maxHeap = new PriorityQueue<>(
            (a, b) -> b.getValue() - a.getValue()
        );

        maxHeap.addAll(map.entrySet());

        for (int i = 0; i < k; i++) {
            ans[i] = maxHeap.poll().getKey();
        }

        return ans;
    }        
}
```
