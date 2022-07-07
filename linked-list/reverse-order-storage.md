# Reverse Order Storage

[https://www.lintcode.com/problem/822/](https://www.lintcode.com/problem/822/)\


> Description
>
> Give a linked list, and store the values of linked list **in reverse order** into an array.
>
> * You **can not change** the structure of the original linked list.
> * ListNode have two elements: ListNode.val and ListNode.next
>
> Example
>
> **Example1**
>
> ```
> Input: 1 -> 2 -> 3 -> null
> Output: [3,2,1]
> ```
>
> **Example2**
>
> ```
> Input: 4 -> 2 -> 1 -> null
> Output: [1,2,4]
> ```

```
public class Solution {
    /**
     * @param head: the given linked list
     * @return: the array that store the values in reverse order 
     */
    List<Integer> res = new ArrayList();
    public List<Integer> reverseStore(ListNode head) {
        reverse(head);
        return res;
    }
    private void reverse(ListNode head){
        if(head == null) return;
        reverse(head.next);
        res.add(head.val);
    }
}
```
