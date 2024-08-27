# Problem Statement

Given an array of integers `temperatures` represents the daily temperatures, return an array `answer` such that `answer[i]` is the number of days you have to wait after the `i`th day to get a warmer temperature. If there is no future day for which this is possible, keep `answer[i] == 0` instead.

## Example 1:

**Input:** 
temperatures = [73, 74, 75, 71, 69, 72, 76, 73]

**Output:**
[1, 1, 4, 2, 1, 1, 0, 0]

## Constraints:

- 1 <= temperatures.length <= 105
  
- 30 <= temperatures[i] <= 100

## Approach

We use a stack to store the indices of the temperatures array. We then iterate through the array, and for each temperature, we check if it is greater than the temperature at the index stored at the top of the stack. If it is, we pop the index from the stack and calculate the difference between the current index and the popped index to determine the number of days until a warmer temperature. We continue this process until the stack is empty or the current temperature is not greater than the temperature at the index stored at the top of the stack. Finally, we push the current index onto the stack. 

## Time Complexity:

The time complexity of this approach is **O(n)**, where **n** is the length of the `temperatures` array. This is because each element is pushed and popped from the stack at most once.

## Space Complexity:

The space complexity of this approach is **O(n)**, where **n** is the length of the `temperatures` array. This is due to the space required for the stack and the result array.

```java
class Solution {
    public int[] dailyTemperatures(int[] temperatures) {
        Stack<Integer> stack = new Stack<>();
        int[] res = new int[temperatures.length];

        for(int i = 0; i < temperatures.length; i++){
            while(!stack.isEmpty() && temperatures[i] > temperatures[stack.peek()]){
                int index = stack.pop();
                res[index] = i - index;
            }            
            stack.push(i);
        }
        return res;
    }
}
```
