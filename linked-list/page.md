---
description: Partition List
---

# Page

[https://leetcode.com/problems/partition-list/description/](https://leetcode.com/problems/partition-list/description/)

> Given the `head` of a linked list and a value `x`, partition it such that all nodes **less than** `x` come before nodes **greater than or equal** to `x`.
>
> You should **preserve** the original relative order of the nodes in each of the two partitions.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/01/04/partition.jpg)
>
> <pre><code><strong>Input: head = [1,4,3,2,5,2], x = 3
> </strong><strong>Output: [1,2,2,4,3,5]
> </strong></code></pre>
>
> **Example 2:**
>
> <pre><code><strong>Input: head = [2,1], x = 2
> </strong><strong>Output: [1,2]
> </strong></code></pre>

<pre><code><strong>class Solution {
</strong>    public ListNode partition(ListNode head, int x) {
        if (head == null) return null;
        ListNode beforeHead = new ListNode(0);
        ListNode before = beforeHead;
        ListNode afterHead = new ListNode(0);
        ListNode after = afterHead;

        while (head != null) {
            if (head.val &#x3C; x) {
                before.next = head;
                before = before.next;
            } else {
                after.next = head;
                after = after.next;
            }
            head = head.next;
        }
        after.next = null;
        before.next = afterHead.next;
        return beforeHead.next;
    }
}
</code></pre>
