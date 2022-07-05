# Convert Linked List to Array List / Convert Array List to Linked List

> Convert a linked list to an array list.
>
> Example
>
> **Example 1:**
>
> ```
> Input: 1->2->3->null
> Output: [1,2,3]
> ```
>
> **Example 2:**
>
> ```
> Input: 3->5->8->null
> Output: [3,5,8]
> ```

```
/**
 * Definition for ListNode
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */

public class Solution {
    /**
     * @param head: the head of linked list.
     * @return: An integer list
     */
    public List<Integer> toArrayList(ListNode head) {
        List<Integer> res = new ArrayList<>();
        ListNode cur = head;
        while(cur != null){
            res.add(cur.val);
            cur = cur.next;
        }
        return res;
    }
}
```



> Convert an array list to a linked list.
>
> Example
>
> Example 1:
>
> ```
> Input: [1,2,3,4], 
> Output: 1->2->3->4->null.
> ```
>
> Example 2:
>
> ```
> Input: [1,2], 
> Output: 1->2->null.
> ```

```
/**
 * Definition for ListNode
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */

public class Solution {
    /**
     * @param nums: an integer array
     * @return: the first node of linked list
     */
    public ListNode toLinkedList(List<Integer> nums) {
        if(nums == null || nums.size() == 0) return null;
        ListNode head = null;
        ListNode temp = null;
        for(int num : nums){
            ListNode cur = new ListNode(num);
            if(head == null){
                head = cur;
                temp = head;
            } else {
                temp.next = cur;
                temp = temp.next;
            }
        }
        return head;
    }
}
```
