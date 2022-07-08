# Invert Binary Tree

[https://leetcode.com/problems/invert-binary-tree/](https://leetcode.com/problems/invert-binary-tree/)

> Given the `root` of a binary tree, invert the tree, and return _its root_.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/03/14/invert1-tree.jpg)
>
> ```
> Input: root = [4,2,7,1,3,6,9]
> Output: [4,7,2,9,6,3,1]
> ```
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2021/03/14/invert2-tree.jpg)
>
> ```
> Input: root = [2,1,3]
> Output: [2,3,1]
> ```

```
class Solution {
    public TreeNode invertTree(TreeNode root) {
        if(root == null) return root;
        TreeNode left = invertTree(root.left);
        TreeNode right = invertTree(root.right);
        
        root.left = right;
        root.right = left;
        return root;
    }
}
```
