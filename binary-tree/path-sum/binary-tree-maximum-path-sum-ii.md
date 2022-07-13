# Binary Tree Maximum Path Sum II

求二叉树中从根向下的和最大的一条路径

> Description
>
> Given a binary tree, find the maximum path sum from root.
>
> The path may end at any node in the tree and contain at least one node (that is,the root node) in it.
>
> Example
>
> **Example 2:**
>
> ```
> Input: {1,-1,-1}
> Output: 1
> Explanation:
>     1
>    / \
>   -1 -1
> ```
>
> ****
>
> **Example 1:**
>
> ```
> Input: {1,2,3}
> Output: 4
> Explanation:
>     1
>    / \
>   2   3
> 1+3=4
> ```

{% hint style="info" %}
根节点，向下的和最大的路径有三种选择&#x20;

– 根节点本身&#x20;

– 根节点加上左子树向下和最大的路径&#x20;

– 根节点加上右子树向下和最大的路径
{% endhint %}

```
public class Solution {

    public int maxPathSum2(TreeNode root) {
        if(root == null) return 0;
        int left = maxPathSum2(root.left);
        int right = maxPathSum2(root.right);
        return root.val + Math.max(Math.max(left, right), 0);
    }
}
```

