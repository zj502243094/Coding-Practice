# Palindrome Linked List

[https://leetcode.com/problems/palindrome-linked-list/](https://leetcode.com/problems/palindrome-linked-list/)

> Given the `head` of a singly linked list, return `true` _if it is a palindrome or_ `false` _otherwise_.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/03/03/pal1linked-list.jpg)
>
> <pre><code>Input: head = [1,2,2,1]
> <strong>Output:
> </strong> true</code></pre>
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2021/03/03/pal2linked-list.jpg)
>
> <pre><code>Input: head = [1,2]
> <strong>Output:
> </strong> false</code></pre>
>
> **Follow up:** Could you do it in `O(n)` time and `O(1)` space?

```
class Solution {
    public boolean isPalindrome(ListNode head) {
        ListNode mid = findMid(head);
        ListNode end = reverse(mid);
        ListNode p1 = head;
        ListNode p2 = end;
        while (p1 != null && p2 != null) {
            if (p1.val != p2.val) return false;
            p1 = p1.next;
            p2 = p2.next;
        }
        // mid.next = reverse(end);
        return true;
    }
    private ListNode findMid(ListNode head) {
        ListNode fast = head;
        ListNode slow = head;
        while (fast.next != null && fast.next.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;
    } 
    private ListNode reverse(ListNode head) {
        ListNode prev = null;
        while (head != null) {
            ListNode next = head.next;
            head.next = prev;
            prev = head;
            head = next;
        }
        return prev;
    }
}
```
