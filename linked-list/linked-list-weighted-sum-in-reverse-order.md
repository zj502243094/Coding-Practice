# Linked List Weighted Sum In Reverse Order

[https://www.lintcode.com/problem/786/](https://www.lintcode.com/problem/786/)\


```
public class Solution {
    /**
     * @param head: the given linked list
     * @return:  the weighted sum in reverse order
     */
    int sum = 0;
    public int weightedSumReverse(ListNode head) {
        weight(head);
        return sum;
    }
    private int weight(ListNode head){
        if(head == null) return 0;
        int dist = 1 + weight(head.next);
        sum += head.val * dist;
        return dist;
    }
}
```
