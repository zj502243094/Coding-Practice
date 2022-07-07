# Linked List Weighted Sum In Reverse Order

[https://www.lintcode.com/problem/786/](https://www.lintcode.com/problem/786/)\


> Description
>
> Given a linked list, output the weighted sum in reverse order. The weight is the number of nodes up to the end of the queue.
>
> Example
>
> **Example1**
>
> ```
> Input: 3 -> 2 -> 5 -> 1
> Output: 29
> Explanation:
> (3 * 4 + 2 * 3 + 5 * 2 + 1) = 29
> ```
>
> **Example2**
>
> ```
> Input: 1 -> 2 -> 3 -> 4
> Output: 20
> Explanation:
> (1 * 4 + 2 * 3 + 3 * 2 + 4) = 20
> ```

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
