# Merge k Sorted Lists

[https://leetcode.com/problems/merge-k-sorted-lists/](https://leetcode.com/problems/merge-k-sorted-lists/)

{% hint style="info" %}
将ListNode 头节点 加入 最小堆 \
如果头结点比较后 cur.next 不为空 继续加入到PQ中
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
    public ListNode mergeKLists(ListNode[] lists) {
        if (lists == null || lists.length == 0) return null;
        ListNode dummy = new ListNode(0);
        ListNode cur = dummy;
        
        PriorityQueue<ListNode> pq = new PriorityQueue<ListNode>((a, b) -> (a.val - b.val));
        for (ListNode list : lists) {
            if (list != null) {
                pq.offer(list);
            }
        }
        
        while (pq.size() > 0) {
            cur.next = pq.poll();
            cur = cur.next;
            if (cur.next != null) {
                pq.offer(cur.next);
            }
        }
        return dummy.next;
    }
}
```
