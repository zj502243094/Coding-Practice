# Balanced Binary Tree

[https://leetcode.com/problems/balanced-binary-tree/](https://leetcode.com/problems/balanced-binary-tree/)

> Given a binary tree, determine if it is height-balanced.
>
> For this problem, a height-balanced binary tree is defined as:
>
> > a binary tree in which the left and right subtrees of _every_ node differ in height by no more than 1.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2020/10/06/balance\_1.jpg)
>
> ```
> Input: root = [3,9,20,null,null,15,7]
> Output: true
> ```
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2020/10/06/balance\_2.jpg)
>
> ```
> Input: root = [1,2,2,3,3,null,null,4,4]
> Output: false
> ```

```
class Solution {
    boolean balanced = true;
    public boolean isBalanced(TreeNode root) {
        if(root == null) return true;
        maxDep(root);
        return balanced;
    }
    
    private int maxDep(TreeNode root){
        if(root == null) return 0;
        int left = maxDep(root.left);
        int right = maxDep(root.right);
        int max = Math.max(left, right) + 1;
        if(Math.abs(left - right) > 1) balanced = false;
        return max;
    }
}
```
