# Odd Even Linked List

[https://leetcode.com/problems/odd-even-linked-list/description/](https://leetcode.com/problems/odd-even-linked-list/description/)

> Given the `head` of a singly linked list, group all the nodes with odd indices together followed by the nodes with even indices, and return _the reordered list_.
>
> The **first** node is considered **odd**, and the **second** node is **even**, and so on.
>
> Note that the relative order inside both the even and odd groups should remain as it was in the input.
>
> You must solve the problem in `O(1)` extra space complexity and `O(n)` time complexity.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/03/10/oddeven-linked-list.jpg)
>
> <pre><code><strong>Input: head = [1,2,3,4,5]
> </strong><strong>Output: [1,3,5,2,4]
> </strong></code></pre>
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2021/03/10/oddeven2-linked-list.jpg)
>
> <pre><code><strong>Input: head = [2,1,3,5,6,4,7]
> </strong><strong>Output: [2,3,6,7,1,5,4]
> </strong></code></pre>

{% hint style="info" %}
Based on index checking even and odd.
{% endhint %}

```
class Solution {
    public ListNode oddEvenList(ListNode head) {
        if (head == null || head.next == null) return head; 

        ListNode odd = head, even = head.next;
        ListNode evenHead = even;

        while (even != null && even.next != null) {
            odd.next = even.next;
            odd = odd.next;
            even.next = odd.next;
            even = even.next;
        }
        odd.next = evenHead;
        return head;
    }
}
```
