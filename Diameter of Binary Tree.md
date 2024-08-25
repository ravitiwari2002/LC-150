# [Problem](https://leetcode.com/problems/diameter-of-binary-tree/)
Given the root of a binary tree, return the length of the diameter of the tree.

The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.

The length of a path between two nodes is represented by the number of edges between them.

## Example 1:
Input: root = [1,2,3,4,5]
Output: 3
Explanation: 3 is the length of the path [4,2,1,3] or [5,2,1,3].

## Example 2:
Input: root = [1,2]
Output: 1


## Constraints:

- The number of nodes in the tree is in the range [1, 10^4].
- -100 <= Node.val <= 100

## Optimal Approach

To find the diameter of the binary tree, we perform a Depth-First Search (DFS) traversal and keep track of the maximum diameter found at each node. The diameter at each node is the sum of the height of the left and right subtrees. The function `dfs` calculates the height of a subtree and updates the maximum diameter (`ans`).

**Time Complexity:** O(n), where n is the number of nodes in the binary tree.  
**Space Complexity:** O(h), where h is the height of the binary tree (due to recursion stack).

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
    int ans = 0;
    
    public int diameterOfBinaryTree(TreeNode root) {
        dfs(root);
        return ans;
    }

    public int dfs(TreeNode root) {
        if (root == null) {
            return 0;
        }

        int left = dfs(root.left);
        int right = dfs(root.right);

        ans = Math.max(ans, left + right);

        return 1 + Math.max(left, right);
    }
}
```

