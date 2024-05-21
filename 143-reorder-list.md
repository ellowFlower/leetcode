# 143. Reorder List
The idea is to adapt the node pointers while going through the list from the start and end simultaneously.

The implementation consists of three parts:

**Place pointers**

One pointer (`slow`) is placed to the last node of the list's first half, and another pointer (`fast`) is placed to the last node of the list.

**Reverse second half of the list**

Because, in the last stage of the solution, the second half of the list is traversed backwards, the node pointers are reversed.

**Merge two halfs**

The two halfs of the list are merged to result in the desired outcome.
## Code
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
    public void reorderList(ListNode head) {
        var slow = head;
        var fast = head.next;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        // slow points to last node of first half
        // fast points to last node of whole list

        // reverse second part of list because we want to go backwards later
        var currentNode = slow.next;  // points to beginning of second half of list
        slow.next = null;
        ListNode prevNode = null;
        while (currentNode != null) {
            var tmp = currentNode.next;
            currentNode.next = prevNode;
            prevNode = currentNode;
            currentNode = tmp;
        }

        // merge two parts
        var first = head; // points to first node
        var second = prevNode; // points to last node in list
        while (second != null) {
            var firstNextTmp = first.next;
            var secondNextTmp = second.next;
            // update pointers
            first.next = second;
            second.next = firstNextTmp;
            // move through list
            first = firstNextTmp;
            second = secondNextTmp;
        }
    }
}
```
