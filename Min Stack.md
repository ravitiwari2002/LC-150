## [Problem: MinStack](https://leetcode.com/problems/min-stack/)

Design a stack that supports `push`, `pop`, `top`, and retrieving the minimum element in constant time.

Implement the `MinStack` class:

- `MinStack()` initializes the stack object.
- `void push(int val)` pushes the element `val` onto the stack.
- `void pop()` removes the element on the top of the stack.
- `int top()` gets the top element of the stack.
- `int getMin()` retrieves the minimum element in the stack.

You must implement a solution with **O(1)** time complexity for each function.

### Example 1:

**Input:**
["MinStack","push","push","push","getMin","pop","top","getMin"]
[[],[-2],[0],[-3],[],[],[],[]]

**Output**
[null,null,null,null,-3,null,0,-2]

### Optimal Approach

We use two stacks to keep track of the minimum value in the stack. Whenever the minimum value is popped out, we pop it from both stacks.

**Time Complexity:** O(1) for each operation.  
**Space Complexity:** O(n) where n is the number of elements pushed onto the stack.

```java
class MinStack {
    private Stack<Integer> stack;
    private Stack<Integer> min;

    public MinStack() {
        stack = new Stack<>();
        min = new Stack<>();
    }
    
    public void push(int val) {
        if (min.isEmpty() || val <= min.peek()) {
            min.push(val);
        }
        stack.push(val);
    }
    
    public void pop() {
        if (stack.peek().equals(min.peek())) {
            min.pop();
        }
        stack.pop();
    }
    
    public int top() {
        return stack.peek();
    }
    
    public int getMin() {
        return min.peek();
    }
}
```

