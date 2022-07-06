# Copy List with Random Pointer

[https://leetcode.com/problems/copy-list-with-random-pointer/](https://leetcode.com/problems/copy-list-with-random-pointer/)

\[1 -> 2 -> 3] \[1 => 3]   to \[1' -> 2' -> 3'] \[1' => 3']   deep copy

> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2019/12/18/e1.png)
>
> ```
> Input: head = [[7,null],[13,0],[11,4],[10,2],[1,0]]
> Output: [[7,null],[13,0],[11,4],[10,2],[1,0]]
> ```
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2019/12/18/e2.png)
>
> ```
> Input: head = [[1,1],[2,1]]
> Output: [[1,1],[2,1]]
> ```
>
> **Example 3:**
>
> ![](https://assets.leetcode.com/uploads/2019/12/18/e3.png)
>
> ```
> Input: head = [[3,null],[3,0],[3,null]]
> Output: [[3,null],[3,0],[3,null]]
> ```

{% hint style="info" %}
1. \[1 ->1' -> 2 ->2' -> 3]    copy next&#x20;
2. \[1 => 3] \[1' => 3']   copy random
3. split \[1 ->1' -> 2 ->2' -> 3] to \[1' -> 2' -> 3']&#x20;
{% endhint %}

```
/*
// Definition for a Node.
class Node {
    int val;
    Node next;
    Node random;

    public Node(int val) {
        this.val = val;
        this.next = null;
        this.random = null;
    }
}
*/

class Solution {
    public Node copyRandomList(Node head) {
        if(head == null) return null;
        copyNext(head);
        copyRandom(head);
        return splitList(head);
    }
    private void copyNext(Node head){
        while(head != null){
            Node newNode = new Node(head.val);
            newNode.next = head.next;
            head.next = newNode;
            head = newNode.next;
        }
    }
    private void copyRandom(Node head){
        while(head != null){
            if(head.random != null){
                head.next.random = head.random.next;
            }
            head = head.next.next;
        }
    }
    private Node splitList(Node head){
        // [1 ->1' -> 2 ->2' -> 3]
        Node newNode = head.next;
        while(head != null){
            Node tmp = head.next;
            head.next = tmp.next;
            if(tmp.next != null){
                tmp.next = tmp.next.next;
            }
            head = head.next;
        }
        return newNode;
    }
}
```
