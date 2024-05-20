# 21. Merge Two Sorted Lists
The idea is to go through both input lists and always add the node with the smaller value to the result list.

The implementation adds the node with the smaller value within a while loop. After all nodes of one input list is are added to the result, the remain of the other input list is appended.
## Code
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 * int val;
 * ListNode next;
 * ListNode() {}
 * ListNode(int val) { this.val = val; }
 * ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode result = new ListNode();
        var tmp = result;
        
        while (list1 != null && list2 != null) {
            if (list1.val <= list2.val) {
                tmp.next = list1;
                list1 = list1.next;
            } else {
                tmp.next = list2;
                list2 = list2.next;
            }
            tmp = tmp.next;
        }

        if (list1 != null) {
            tmp.next = list1;
        }
        if (list2 != null) {
            tmp.next = list2;
        }

        return result.next;
    }
}
```
