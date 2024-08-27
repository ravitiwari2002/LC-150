# [Problem Statement](https://leetcode.com/problems/balanced-binary-tree/)

Given a binary tree, determine if it is height-balanced.

A height-balanced binary tree is a binary tree in which the depth of the two subtrees of every node never differs by more than one.

## Example 1
![image](https://github.com/user-attachments/assets/96b00243-a071-48f2-907a-77d9bbcb82be)

## Output: true

## Example 2

![image](https://github.com/user-attachments/assets/f83763f3-2126-438e-a847-4d259fbf7719)

## Output: false

## Approach

To determine if the binary tree is height-balanced, we use a Depth-First Search (DFS) approach. We maintain a global variable `ans` to keep track of whether the tree is balanced. The DFS function calculates the height of each subtree and checks the absolute difference between the heights of the left and right subtrees. If at any node, this difference is greater than 1, the tree is not balanced.

### Time Complexity and Space Complexity

- **Time Complexity:** O(n), where `n` is the number of nodes in the binary tree. We traverse each node once.
- **Space Complexity:** O(h), where `h` is the height of the binary tree. This is the space required for the recursion stack.

## Java Code

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {

    Boolean ans = true;

    public boolean isBalanced(TreeNode root) {
        dfs(root);
        return ans;
    }

    public int dfs(TreeNode root) {
        if (root == null) {
            return 0;
        }

        int left = dfs(root.left);
        int right = dfs(root.right);

        if (Math.abs(left - right) > 1) {
            ans = false;
        }

        return 1 + Math.max(left, right);
    }
}
``` 
