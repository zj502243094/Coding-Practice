# Binary Tree Maximum Path Sum

[https://leetcode.com/problems/binary-tree-maximum-path-sum/](https://leetcode.com/problems/binary-tree-maximum-path-sum/)

求二叉树中从任意 开始/  结束的和为 最大的一条路径

> A **path** in a binary tree is a sequence of nodes where each pair of adjacent nodes in the sequence has an edge connecting them. A node can only appear in the sequence **at most once**. Note that the path does not need to pass through the root.
>
> The **path sum** of a path is the sum of the node's values in the path.
>
> Given the `root` of a binary tree, return _the maximum **path sum** of any **non-empty** path_.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2020/10/13/exx1.jpg)
>
> ```
> Input: root = [1,2,3]
> Output: 6
> Explanation: The optimal path is 2 -> 1 -> 3 with a path sum of 2 + 1 + 3 = 6.
> ```
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2020/10/13/exx2.jpg)
>
> ```
> Input: root = [-10,9,20,null,null,15,7]
> Output: 42
> Explanation: The optimal path is 15 -> 20 -> 7 with a path sum of 15 + 20 + 7 = 42.
> ```

{% hint style="info" %}
traversal every nodes as the top of sub tree

根节点，和最大的路径有三种选择&#x20;

– 左子树中和最大的路径&#x20;

– 右子树中和最大的路径&#x20;

– 左子树中和最大的单路径+右子树中和最大的单路径+根节点的值
{% endhint %}

```
class Solution {
    int maxSum = Integer.MIN_VALUE;
    public int maxPathSum(TreeNode root) {
        getMax(root);
        return maxSum;
    }
    private int getMax(TreeNode p){
        if(p == null) return 0;
        int left = getMax(p.left);
        int right = getMax(p.right);
        
        maxSum = Math.max(maxSum, p.val);
        maxSum = Math.max(maxSum, left + p.val);
        maxSum = Math.max(maxSum, right + p.val);
        maxSum = Math.max(maxSum, left + right + p.val);
        return Math.max(Math.max(left, right), 0) + p.val;
    }
}
```
