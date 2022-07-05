# Merge Two Sorted Lists

[https://leetcode.com/problems/merge-two-sorted-lists/](https://leetcode.com/problems/merge-two-sorted-lists/)

> You are given the heads of two sorted linked lists `list1` and `list2`.
>
> Merge the two lists in a one **sorted** list. The list should be made by splicing together the nodes of the first two lists.
>
> Return _the head of the merged linked list_.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2020/10/03/merge\_ex1.jpg)
>
> ```
> Input: list1 = [1,2,4], list2 = [1,3,4]
> Output: [1,1,2,3,4,4]
> ```
>
> **Example 2:**
>
> ```
> Input: list1 = [], list2 = []
> Output: []
> ```
>
> **Example 3:**
>
> ```
> Input: list1 = [], list2 = [0]
> Output: [0]
> ```

```
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        if(list1 == null && list2 == null) return null;
        
        ListNode dummy = new ListNode(0);
        ListNode cur = dummy;
        while(list1 != null && list2 != null){
            if(list1.val <= list2.val){
                cur.next = list1;
                list1 = list1.next;
            }else{
                cur.next = list2;
                list2 = list2.next;
            }
            cur = cur.next;
        }
        if(list1 != null){
            cur.next = list1;
        }else{
            cur.next = list2;
        }
        return dummy.next;
    }
}
```
