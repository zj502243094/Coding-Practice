# Remove Nth Node From End of List

[https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)

> Given the `head` of a linked list, remove the `nth` node from the end of the list and return its head.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2020/10/03/remove_ex1.jpg)
>
> <pre><code><strong>Input: head = [1,2,3,4,5], n = 2
> </strong><strong>Output: [1,2,3,5]
> </strong></code></pre>
>
> **Example 2:**
>
> <pre><code><strong>Input: head = [1], n = 1
> </strong><strong>Output: []
> </strong></code></pre>
>
> **Example 3:**
>
> <pre><code><strong>Input: head = [1,2], n = 1
> </strong><strong>Output: [1]
> </strong></code></pre>

{% hint style="info" %}
Instead of **counting from the end** (which is hard in a singly linked list), we use **two pointers**:

1. **First pointer (`first`)** moves **n+1 steps ahead**.
2. **Second pointer (`second`)** starts from the beginning.
3. Then, both pointers move **one step at a time** until `first` reaches the end.
4. At this point, `second` will be **just before the node we want to delete**.
5. We remove the node by changing `second.next`
{% endhint %}

```
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode first = dummy, second= dummy;

        for (int i = 0; i <= n; i++) {
            first = first.next;
        }
        while (first != null) {
            first = first.next;
            second = second.next;
        }

        second.next = second.next.next;
        
        return dummy.next;
    }
}
```
