# Reverse Linked List

[https://leetcode.com/problems/reverse-linked-list/](https://leetcode.com/problems/reverse-linked-list/)

> Given the `head` of a singly linked list, reverse the list, and return _the reversed list_.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/02/19/rev1ex1.jpg)
>
> ```
> Input: head = [1,2,3,4,5]
> Output: [5,4,3,2,1]
> ```
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2021/02/19/rev1ex2.jpg)
>
> ```
> Input: head = [1,2]
> Output: [2,1]
> ```
>
> **Example 3:**
>
> ```
> Input: head = []
> Output: []
> ```

<img src="../.gitbook/assets/image (1) (1) (1).png" alt="" data-size="original">

```
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode next = null;
        
        while(head != null) {
            next = head.next;
            head.next = prev;
            
            prev = head;
            head = next;
        }
        return prev;
    }
}
```
