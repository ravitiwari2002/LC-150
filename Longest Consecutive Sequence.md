# [Problem Statement](https://leetcode.com/problems/longest-consecutive-sequence/)

Given an unsorted array of integers `nums`, return the length of the longest consecutive elements sequence.

You must write an algorithm that runs in O(n) time.

## Examples

**Example 1:**

- **Input:** `nums = [100, 4, 200, 1, 3, 2]`
- **Output:** `4`
- **Explanation:** The longest consecutive elements sequence is `[1, 2, 3, 4]`. Therefore, its length is 4.

**Example 2:**

- **Input:** `nums = [0, 3, 7, 2, 5, 8, 4, 6, 0, 1]`
- **Output:** `9`

## Constraints

- `0 <= nums.length <= 10^5`
- `-10^9 <= nums[i] <= 10^9`

## Solution

### Brute Force Approach

We sort the array so that it already forms the sequence. We then traverse the array while keeping track of the longest sequence and skipping duplicates.

**Time Complexity:** O(n log n) and **Space Complexity:** O(1) 
```java
class Solution {
    public int longestConsecutive(int[] nums) {
        if (nums.length == 0) 
            return 0;

        Arrays.sort(nums);

        int max = 1;
        int current = 1;

        for (int i = 0; i < nums.length - 1; i++) {
            if (nums[i] != nums[i + 1]) {
                if (nums[i] + 1 == nums[i + 1]) {
                    current++;
                } else {
                    max = Math.max(max, current);
                    current = 1;
                }
            }
        }

        return Math.max(max, current);
    }
}
```

## Optimal Approach

We utilize a HashMap to track the presence of each element in the array, initially setting all values to `false`. The map helps us identify and mark elements as part of a sequence. We iterate through the array and check each element to see if the next and previous numbers in the sequence are present and have not been used yet. If the conditions are met, we increment the sequence length accordingly and update the map. We continue this process for all elements to find the maximum sequence length.

**Time Complexity:** O(n) and **Space Complexity:** O(n)
```java
class Solution {
    public int longestConsecutive(int[] nums) {
        Map<Integer, Boolean> map = new HashMap<>();

        for (int num : nums) {
            map.put(num, false);
        }

        int max_sequence = 0;

        for (int i = 0; i < nums.length; i++) {
            int curr_sequence = 1;
            int next = nums[i] + 1;

            while (map.containsKey(next) && map.get(next) == false) {
                curr_sequence++;
                map.put(next, true);
                next++;
            }

            int prev = nums[i] - 1;
            while (map.containsKey(prev) && map.get(prev) == false) {
                curr_sequence++;
                map.put(prev, true);
                prev--;
            }

            max_sequence = Math.max(max_sequence, curr_sequence);
        }

        return max_sequence;
    }
}
```
