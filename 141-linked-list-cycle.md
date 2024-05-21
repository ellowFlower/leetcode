# 141. Linked List Cycle
The idea is to go through the list, remember which nodes were visited, and check if a node is visited the second time.

The implementation uses a hash set to remember visited nodes and a while loop to go through the list.
## Code
```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {
        var n = new HashSet<ListNode>();
        while (head != null) {
            if (head.next != null) {
                if (n.contains(head.next)) {
                    return true;
                }
                n.add(head.next);
            }
            head = head.next;
        }
        return false;
    }
}
```
