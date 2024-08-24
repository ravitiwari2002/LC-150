## Problem Statement

Given the root of a binary tree, invert the tree, and return its root.

### Example 1

![image](https://github.com/user-attachments/assets/a9ecbb52-47e6-4ac7-9c7a-8b30ac62b0d8)

Input: root = [4,2,7,1,3,6,9]
Output: [4,7,2,9,6,3,1]

### Example 2

![image](https://github.com/user-attachments/assets/44bc25a7-6334-41a8-9651-cd948feaf03a)

Input: root = [2,1,3]
Output: [2,3,1]

### Example 3
Input: root = []
Output: []

### Constraints

- The number of nodes in the tree is in the range [0, 100].
- -100 <= Node.val <= 100

## Approach

To solve this problem, we need to swap every node's children such that the left child becomes the right child and the right child becomes the left child. This can be achieved recursively by performing the following steps:

1. **Base Case**: If the current node (`root`) is `null`, return `null` because there's nothing to invert.
2. **Swap Children**: Swap the left and right children of the current node.
3. **Recursive Inversion**: Recursively call the function on the left and right children to continue inverting the tree down the structure.
4. **Return the Root**: After inverting the entire tree, return the root node.

### Time Complexity

- **O(n)**: The time complexity is O(n), where n is the number of nodes in the binary tree. Each node is visited exactly once.

### Space Complexity

- **O(h)**: The space complexity is O(h), where h is the height of the binary tree. This space is used by the recursion stack. In the worst case, the height of the binary tree could be equal to the number of nodes, resulting in O(n) space complexity for a skewed tree. For a balanced tree, this would be O(log n).

## Solution Code

```java
class Solution {
    public TreeNode invertTree(TreeNode root) {
        if (root == null) {
            return null;
        }

        // Swap the left and right children
        TreeNode tmp = root.left;
        root.left = root.right;
        root.right = tmp;

        // Recursively invert the left and right subtrees
        invertTree(root.left);
        invertTree(root.right);

        return root;
    }
}
```
