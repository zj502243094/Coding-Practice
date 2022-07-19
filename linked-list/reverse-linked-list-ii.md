# Reverse Linked List II

[https://leetcode.com/problems/reverse-linked-list-ii/](https://leetcode.com/problems/reverse-linked-list-ii/)

> Given the `head` of a singly linked list and two integers `left` and `right` where `left <= right`, reverse the nodes of the list from position `left` to position `right`, and return _the reversed list_.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/02/19/rev2ex2.jpg)
>
> ```
> Input: head = [1,2,3,4,5], left = 2, right = 4
> Output: [1,4,3,2,5]
> ```
>
> **Example 2:**
>
> ```
> Input: head = [5], left = 1, right = 1
> Output: [5]
> ```

{% hint style="info" %}
1. find reverse head;
2. reverse sublist;\
   ![](<../.gitbook/assets/image (5) (1).png>)
3. connect new sub Linked List\
   ![](<../.gitbook/assets/image (1) (1).png>)
{% endhint %}

```
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
    public ListNode reverseBetween(ListNode head, int left, int right) {
        if(head == null) return head;
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        
        ListNode reverseHead = dummy;
        for(int i = 1; i < left; i++){
            reverseHead = reverseHead.next;
        }
        ListNode prev = reverseHead.next;
        ListNode cur = prev.next;
        ListNode front = reverseHead;
        ListNode end = reverseHead.next; 
        
        for(int i = left; i < right; i++){
            ListNode next = cur.next;
            cur.next = prev;
            
            prev = cur;
            cur = next;
        }
        front.next = prev;
        end.next = cur;
        return dummy.next;
    }
}
```



