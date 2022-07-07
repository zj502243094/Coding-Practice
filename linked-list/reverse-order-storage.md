# Reverse Order Storage

[https://www.lintcode.com/problem/822/](https://www.lintcode.com/problem/822/)\


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
