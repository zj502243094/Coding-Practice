# Validate Binary Search Tree

[https://leetcode.com/problems/validate-binary-search-tree/](https://leetcode.com/problems/validate-binary-search-tree/)

> Given the `root` of a binary tree, _determine if it is a valid binary search tree (BST)_.
>
> A **valid BST** is defined as follows:
>
> * The left subtree of a node contains only nodes with keys **less than** the node's key.
> * The right subtree of a node contains only nodes with keys **greater than** the node's key.
> * Both the left and right subtrees must also be binary search trees.

```
class Solution {
    public boolean isValidBST(TreeNode root) {
        return check(root, Long.MIN_VALUE, Long.MAX_VALUE);
    }
    private boolean check(TreeNode root, long min, long max){
        if(root == null) return true;
        if(root.val <= min || root.val >= max) return false;
        return check(root.left, min, root.val) && check(root.right, root.val, max);
    }
}
```
