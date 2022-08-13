# Intersection of Two Linked Lists

[https://leetcode.com/problems/intersection-of-two-linked-lists/](https://leetcode.com/problems/intersection-of-two-linked-lists/)

> Given the heads of two singly linked-lists `headA` and `headB`, return _the node at which the two lists intersect_. If the two linked lists have no intersection at all, return `null`.
>
>
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/03/05/160\_example\_1\_1.png)
>
> ```
> Input: intersectVal = 8, listA = [4,1,8,4,5], listB = [5,6,1,8,4,5], skipA = 2, skipB = 3
> ```

{% hint style="info" %}
遍历A 和B
{% endhint %}

```
public  class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        if(headA == null || headB == null) return null;
        while (headA != null) {
            ListNode cur = headB;
            while (cur != null) {
                if (cur == headA) {
                    return cur;
                }
                cur = cur.next;
            }
            headA = headA.next;
        }
        return null;
    }
}
```

{% hint style="info" %}
将两个list结合起来 一个从 A开始 走 A +B 一个从B开始走B+A 剩下最后的几步是共同

**Time :** O( m + n )  **Space:** O(1)
{% endhint %}

```
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        if (headA == null || headB == null) return null;
        ListNode node1 = headA;
        ListNode node2 = headB;
        while (node1 != node2) {
            node1 = node1.next;
            node2 = node2.next;
            if (node1 == node2) return node1;
            if (node1 == null) node1 = headB; 
            if (node2 == null) node2 = headA;
        }
        return node1;
    }
}
```

![](<../.gitbook/assets/image (5).png>)
