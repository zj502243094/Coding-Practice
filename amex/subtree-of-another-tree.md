# Subtree of Another Tree

> Given the roots of two binary trees `root` and `subRoot`, return `true` if there is a subtree of `root` with the same structure and node values of `subRoot` and `false` otherwise.
>
> A subtree of a binary tree `tree` is a tree that consists of a node in `tree` and all of this node's descendants. The tree `tree` could also be considered as a subtree of itself.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/04/28/subtree1-tree.jpg)
>
> ```
> Input: root = [3,4,5,1,2], subRoot = [4,1,2]
> Output: true
> ```
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2021/04/28/subtree2-tree.jpg)
>
> ```
> Input: root = [3,4,5,1,2,null,null,null,null,0], subRoot = [4,1,2]
> Output: false
> ```

```
class Solution {
    public boolean isSubtree(TreeNode root, TreeNode subRoot) {
        if(root == null || subRoot == null) return root == subRoot;
        if(isSame(root, subRoot)) return true;
        return isSubtree(root.left, subRoot) || isSubtree(root.right, subRoot);
    }
    private boolean isSame(TreeNode p, TreeNode q){
        if(p == null || q == null) return p == q;
        if(p.val != q.val) return false;
        return isSame(p.left, q.left) && isSame(p.right, q.right);
    }
}
```
