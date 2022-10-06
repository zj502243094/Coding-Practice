# Next Greater Node In Linked List

[https://leetcode.com/problems/next-greater-node-in-linked-list/](https://leetcode.com/problems/next-greater-node-in-linked-list/)

> You are given the `head` of a linked list with `n` nodes.
>
> For each node in the list, find the value of the **next greater node**. That is, for each node, find the value of the first node that is next to it and has a **strictly larger** value than it.
>
> Return an integer array `answer` where `answer[i]` is the value of the next greater node of the `ith` node (**1-indexed**). If the `ith` node does not have a next greater node, set `answer[i] = 0`.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/08/05/linkedlistnext1.jpg)
>
> <pre><code>Input: head = [2,1,5]
> <strong>Output:
> </strong> [5,5,0]</code></pre>
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2021/08/05/linkedlistnext2.jpg)
>
> <pre><code>Input: head = [2,7,4,3,5]
> <strong>Output:
> </strong> [7,0,5,5,0]</code></pre>

```
class Solution {
    public int[] nextLargerNodes(ListNode head) {
        List<Integer> nums = new ArrayList<>();
        for (ListNode cur = head; cur != null; cur = cur.next) {
            nums.add(cur.val);
        }
        int[] res = new int[nums.size()];
        Stack<Integer> stack = new Stack<>();
        for (int i = nums.size() - 1; i >= 0; i--) {
            while (!stack.isEmpty() && nums.get(i) >= stack.peek()) stack.pop();
            res[i] = stack.isEmpty() ? 0 : stack.peek();
            stack.push(nums.get(i));
        }
        return res;
    }
}
```
