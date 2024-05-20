# 206. Reverse Linked List
The idea is to change pointers to the next node in the list. They are changed to the previous node in the list.

The implementation can be done recursive or iterative.

**recursive**
This solution calls the method to update a pointer once for every node in the list. If `head.next` is null the last node is reached.

**iterative**
The iterative solution uses a while loop to visit each node in the list. For every node it updates `head.next` to point to the previous node. 
## Code
### recursive
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
        if (head == null) {
            return null;
        }
        return (r(head, null));
    }

    private ListNode r(ListNode head, ListNode prev) {
        if (head.next == null) {
            head.next = prev;
            return head;
        }
        var tmp = head.next;
        head.next = prev;
        return r(tmp, head);
    }
}
```
### iterative
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
        ListNode prev = null;
        while (head != null) {
            var tmp = head.next;
            head.next = prev;
            prev = head;
            head = tmp;
        }
        return prev;
    }
}
```
