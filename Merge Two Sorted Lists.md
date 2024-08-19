## Problem Statement

You are given the heads of two sorted linked lists, `list1` and `list2`. 

Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.

## Approach

- Create a dummy node to simplify edge cases.
- Use a pointer `curr` to traverse and build the merged list.
- Iterate over both `list1` and `list2` while they are not null.
- Compare the values of the nodes in both lists and attach the smaller one to `curr`.
- Move the pointer in the corresponding list to the next node.
- After exiting the loop, attach any remaining nodes from either `list1` or `list2` to the merged list.

- **Time Complexity:** O(n + m) where n and m are the lengths of `list1` and `list2`, respectively.
- **Space Complexity:** O(1)

## Solution Code

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
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode tmp = new ListNode();
        ListNode curr = tmp;

        while(list1 != null && list2 != null) {
            if(list1.val <= list2.val) {
                curr.next = list1;
                list1 = list1.next;
            } else {
                curr.next = list2;
                list2 = list2.next;
            }
            curr = curr.next;
        }

        if(list1 != null) {
            curr.next = list1;
        } else {
            curr.next = list2;
        }

        return tmp.next;
    }
}
```
