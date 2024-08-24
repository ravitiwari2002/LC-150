# [Problem Statement] (https://leetcode.com/problems/maximum-depth-of-binary-tree/)

Given the root of a binary tree, return its depth.

The depth of a binary tree is defined as the number of nodes along the longest path from the root node down to the farthest leaf node.

### Example 1

![image](https://github.com/user-attachments/assets/fbf31fed-f91b-49cd-acc8-950bd19c8cbd)


**Input:** root = [1,2,3,null,null,4]  
**Output:** 3  

**Explanation:** The longest path from the root (1) to the farthest leaf node is [1, 3, 4], which has a length of 3 nodes.

### Example 2

**Input:** root = []  
**Output:** 0  

**Explanation:** An empty tree has a depth of 0 since there are no nodes.

### Constraints

- The number of nodes in the tree is in the range [0, 100].
- -100 <= Node.val <= 100

 ## Approach

To solve this problem, we perform a Depth-First Search (DFS) traversal of the binary tree recursively. For each node, we calculate the depth of its left and right subtrees and return the maximum of these depths plus one (to account for the current node).

### Time Complexity

- **O(n)**, where **n** is the number of nodes in the tree. This is because each node is visited exactly once.

### Space Complexity

- **O(h)**, where **h** is the height of the tree. This space is used by the recursion stack. In the worst case (a skewed tree), the space complexity can be **O(n)**.

### Solution Code

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
    public int maxDepth(TreeNode root) {
        if(root == null){
            return 0;
        }

        return 1 + Math.max(maxDepth(root.left), maxDepth(root.right));
    }
}
``` 
