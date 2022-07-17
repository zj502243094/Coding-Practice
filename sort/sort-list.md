# Sort List

> Given the `head` of a linked list, return _the list after sorting it in **ascending order**_.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2020/09/14/sort\_list\_1.jpg)
>
> ```
> Input: head = [4,2,1,3]
> Output: [1,2,3,4]
> ```
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2020/09/14/sort\_list\_2.jpg)
>
> ```
> Input: head = [-1,5,3,4,0]
> Output: [-1,0,3,4,5]
> ```

{% hint style="info" %}
归并排序 先找到 中间节点 然后 左右2个List 合并
{% endhint %}

```
class Solution {
    public ListNode sortList(ListNode head) {
        if(head == null || head.next == null) return head;
        ListNode mid = findMid(head);
        ListNode right = sortList(mid.next);
        mid.next = null;
        ListNode left = sortList(head);
        return merge(left, right);
    }
    private ListNode findMid(ListNode head){
        ListNode slow = head;
        ListNode fast = head;
        while(fast.next != null && fast.next.next != null){
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;
    }
    private ListNode merge(ListNode l1, ListNode l2){
        ListNode dummy = new ListNode(0);
        ListNode cur = dummy;
        while(l1 != null && l2 != null){
            if(l1.val < l2.val){
                cur.next = l1;
                l1 = l1.next;
            }else{
                cur.next = l2;
                l2 = l2.next;
            }
            cur = cur.next;
        }
        if(l1 != null) cur.next = l1;
        else cur.next = l2;
        return dummy.next;
    }
}
```
