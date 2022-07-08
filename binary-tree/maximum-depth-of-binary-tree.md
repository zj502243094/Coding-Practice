# Maximum Depth of Binary Tree

[https://leetcode.com/problems/maximum-depth-of-binary-tree/](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

> Given the `root` of a binary tree, return _its maximum depth_.
>
> A binary tree's **maximum depth** is the number of nodes along the longest path from the root node down to the farthest leaf node.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2020/11/26/tmp-tree.jpg)
>
> ```
> Input: root = [3,9,20,null,null,15,7]
> Output: 3
> ```

```
class Solution {
    public int maxDepth(TreeNode root) {
        if(root == null) return 0;
        
        int leftMax = maxDepth(root.left);
        int rightMax = maxDepth(root.right);
        
        return Math.max(leftMax, rightMax) + 1;
    }
}
```
