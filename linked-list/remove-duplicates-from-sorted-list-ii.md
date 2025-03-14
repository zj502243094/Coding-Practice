# Remove Duplicates from Sorted List II

[https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/description/](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/description/)

> Given the `head` of a sorted linked list, _delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list_. Return _the linked list **sorted** as well_.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/01/04/linkedlist1.jpg)
>
> <pre><code><strong>Input: head = [1,2,3,3,4,4,5]
> </strong><strong>Output: [1,2,5]
> </strong></code></pre>
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2021/01/04/linkedlist2.jpg)
>
> <pre><code><strong>Input: head = [1,1,1,2,3]
> </strong><strong>Output: [2,3]
> </strong></code></pre>

```
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        if (head == null) return null;
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode prev = dummy;

        while (head != null) {
            if (head.next != null && head.val == head.next.val) {
                while (head.next != null && head.val == head.next.val) {
                    head = head.next;
                }
                prev.next = head.next;
            } else {
                prev = prev.next;
            }
            head = head.next;
        }
        return dummy.next;
    }
}
```
