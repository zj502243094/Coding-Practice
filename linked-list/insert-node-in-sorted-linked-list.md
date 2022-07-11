# Insert Node in Sorted Linked List

> Insert a node in a sorted linked list.
>
> Example
>
> **Example 1:**
>
> ```
> Input: head = 1->4->6->8->null, val = 5
> Output: 1->4->5->6->8->null
> ```
>
> **Example 2:**
>
> ```
> Input: head = 1->null, val = 2
> Output: 1->2->null
> ```

```
public class Solution {
    /**
     * @param head: The head of linked list.
     * @param val: An integer.
     * @return: The head of new linked list.
     */
    public ListNode insertNode(ListNode head, int val) {
        ListNode newNode = new ListNode(val);
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode cur = dummy;

        while(cur.next != null && cur.next.val <= val){
            cur = cur.next;
        }
        newNode.next = cur.next;
        cur.next = newNode;

        return dummy.next;
    }
}

/**
 * Definition for ListNode
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
```
