# Binary Tree Upside Down

[https://leetcode.com/problems/binary-tree-upside-down/](https://leetcode.com/problems/binary-tree-upside-down/)

> Given the `root` of a binary tree, turn the tree upside down and return _the new root_.
>
> You can turn a binary tree upside down with the following steps:
>
> 1. The original left child becomes the new root.
> 2. The original root becomes the new right child.
> 3. The original right child becomes the new left child.
>
> ![](https://assets.leetcode.com/uploads/2020/08/29/main.jpg)
>
> The mentioned steps are done level by level. It is **guaranteed** that every right node has a sibling (a left node with the same parent) and has no children.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2020/08/29/updown.jpg)
>
> ```
> Input: root = [1,2,3,4,5]
> Output: [4,5,2,null,null,3,1]
> ```

{% hint style="info" %}
注意闭环问题&#x20;
{% endhint %}

```
class Solution {
    public TreeNode upsideDownBinaryTree(TreeNode root) {
        if(root == null) return null;
        return upsideDown(root);
    }
    private TreeNode upsideDown(TreeNode cur){
        if(cur.left == null) return cur;
        TreeNode newNode = null;
        newNode = upsideDown(cur.left);
        
        cur.left.right = cur;
        cur.left.left = cur.right;
        
        cur.left = null;
        cur.right = null;
        
        return newNode;
    }
}
```
