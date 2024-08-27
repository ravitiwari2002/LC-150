# [Problem Statement](https://leetcode.com/problems/subtree-of-another-tree/)

Given the roots of two binary trees `root` and `subRoot`, return `true` if there is a subtree of `root` with the same structure and node values of `subRoot` and `false` otherwise.

A subtree of a binary tree `tree` is a tree that consists of a node in `tree` and all of this node's descendants. The tree `tree` could also be considered as a subtree of itself.

## Example 1:

![image](https://github.com/user-attachments/assets/76449132-0375-4bfc-8f74-ae06d1ecb8d1) 

Output: True

## Example 2: ![image](https://github.com/user-attachments/assets/0530d927-196c-4533-b639-e726660ae6c5)

Output: false, because it is not a complete subRoot, subRoot is missing left child of 2. 


## Approach

We use the `isSameTree` function to compare each node in the `root` with the `subRoot`.

## Time Complexity
- The time complexity is \(O(n \times m)\), where \(n\) is the number of nodes in the `root` and \(m\) is the number of nodes in the `subRoot`. This is because, in the worst case, we might need to check every node in the `root` against every node in the `subRoot`.

### Space Complexity
- The space complexity is \(O(h)\), where \(h\) is the height of the `root` tree. This is due to the recursion stack used during the depth-first search.

## Code

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
    public boolean isSubtree(TreeNode root, TreeNode subRoot) {
        if (root == null) {
            return false;
        }

        if (subRoot == null) {
            return true;
        }

        if (isSameTree(root, subRoot)) {
            return true;
        }

        return (isSubtree(root.left, subRoot) || isSubtree(root.right, subRoot));
    }

    public boolean isSameTree(TreeNode p, TreeNode q) {
        if (p == null && q == null) {
            return true;
        }

        if ((p != null && q == null) || (p == null && q != null) || (p.val != q.val)) {
            return false;
        }

        return (isSameTree(p.left, q.left) && isSameTree(p.right, q.right));
    }
}
```
