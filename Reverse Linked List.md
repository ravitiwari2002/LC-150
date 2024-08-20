## [Problem Statement](https://leetcode.com/problems/reverse-linked-list/description/)
You are given the head of a singly linked list. You need to reverse the list and return its new head.

## Approach
The idea is to iterate through the linked list and reverse the direction of the `next` pointers. We can achieve this by using three pointers:

1. **Previous (`prev`)**: This will hold the previous node in the list.
2. **Current (`curr`)**: This will be the node currently being processed.
3. **Next (`nextTemp`)**: This will store the next node temporarily, as the `next` pointer will be reversed.

### Steps:
1. **Initialize Pointers**: Start with `prev` as `null`, `curr` as the head of the list, and `nextTemp` to hold the next node.
2. **Reverse the Pointers**: For each node, store the next node (`nextTemp`), reverse the `next` pointer to point to the previous node (`prev`), and then move the `prev` and `curr` pointers one step forward.
3. **Continue Until End**: Continue the process until you reach the end of the list, where `curr` will become `null`.
4. **Return the New Head**: After the loop, `prev` will be pointing to the new head of the reversed list.

### Time Complexity:
- **Time Complexity**: O(n) where `n` is the number of nodes in the linked list.
- **Space Complexity**: O(1) since we're using only a few extra pointers.

## Java Implementation

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;  // Previous node starts as null
        ListNode curr = head;  // Current node starts as head

        while (curr != null) {  // Traverse until the end of the list
            ListNode nextTemp = curr.next;  // Temporarily store the next node
            curr.next = prev;  // Reverse the current node's pointer
            prev = curr;  // Move prev to the current node
            curr = nextTemp;  // Move to the next node
        }

        return prev;  // New head of the reversed list
    }
}
```
