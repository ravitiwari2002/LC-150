# Problem Statement

Given the roots of two binary trees `p` and `q`, return `true` if the trees are equivalent, otherwise return `false`.

Two binary trees are considered equivalent if they share the exact same structure and the nodes have the same values.

## Example 1

![image](https://github.com/user-attachments/assets/cdf25def-4738-4169-80df-02025fabdc6c)

## Example 2

![image](https://github.com/user-attachments/assets/b39caa63-0116-4b5d-b73f-eb1f6bb56ab5)

## Example 3

![image](https://github.com/user-attachments/assets/ba3c4849-19c3-4cfc-ba1f-caa1bfa3c3ab)

## Approach

1. **Base Case:**  
   - If both tree roots (`p` and `q`) are `null`, return `true` because two `null` trees are considered equivalent.
   - If one of the tree roots is `null` and the other is not, return `false` since the structure is different.

2. **Value Comparison:**  
   - If both tree roots are not `null`, compare their values (`p.val` and `q.val`). If the values are not equal, return `false`.

3. **Recursive Check:**  
   - Recursively call the function `isSameTree` for the left and right children of the current nodes.
   - Use an `AND` condition to ensure that both the left and right subtrees are exactly equal.

### Time Complexity and Space Complexity

- **Time Complexity:** O(n), where `n` is the number of nodes in the smaller tree. In the worst case, we need to visit each node once.
  
- **Space Complexity:** O(h), where `h` is the height of the tree. This is due to the recursion stack space required for a completely unbalanced tree.

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
    public boolean isSameTree(TreeNode p, TreeNode q) {
        // Base cases
        if (p == null && q == null) {
            return true;
        }

        if ((p != null && q == null) || (p == null && q != null) || (p.val != q.val)) {
            return false;
        }

        // Recursive check for left and right subtrees
        return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
    }  
}
```




