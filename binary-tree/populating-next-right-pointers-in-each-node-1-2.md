# Populating Next Right Pointers in Each Node 1 / 2

[https://leetcode.com/problems/populating-next-right-pointers-in-each-node/](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)\
[https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/](https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/)\
1\. 完美BT  (所有的层级都一样 并且每个root 都有两个孩子)所有的node.next 指向右边

> You are given a **perfect binary tree** where all leaves are on the same level, and every parent has two children. The binary tree has the following definition:
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2019/02/14/116\_sample.png)
>
> ```
> Input: root = [1,2,3,4,5,6,7]
> Output: [1,#,2,3,#,4,5,6,7,#]
> Explanation: Given the above perfect binary tree (Figure A), your function should populate each next pointer to point to its next right node, just like in Figure B. The serialized output is in level order as connected by the next pointers, with '#' signifying the end of each level.
> ```
>
> **Example 2:**
>
> ```
> Input: root = []
> Output: []
> ```

```
class Solution {
    public Node connect(Node root) {
        if(root == null) return null;
        if(root.left != null) {
            root.left.next = root.right;
            if(root.next != null){
                root.right.next = root.next.left;
            }
        }
        connect(root.left);
        connect(root.right);
        return root;
    }
}
```

2\. 非完美二叉树

{% hint style="info" %}
先右后左保证最右边的node 都能被连上
{% endhint %}

```
class Solution {
    public Node connect(Node root) {
        if (root == null) return null;
        
        if(root.left != null){
            if(root.right != null) {
                root.left.next = root.right;
            }else{
                root.left.next = findNext(root);
            }
        }
        
        if(root.right != null){
            root.right.next = findNext(root);
        }
        
        connect(root.right);
        connect(root.left);
        return root;
    }
    
    private Node findNext(Node root){
        while(root.next != null){
            root = root.next;
            if(root.left != null) return root.left;
            if(root.right != null) return root.right;
        } 
        return null;
    }
}
```
