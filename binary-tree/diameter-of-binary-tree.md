# Diameter of Binary Tree

> Given the `root` of a binary tree, return _the length of the **diameter** of the tree_.
>
> The **diameter** of a binary tree is the **length** of the longest path between any two nodes in a tree. This path may or may not pass through the `root`.
>
> The **length** of a path between two nodes is represented by the number of edges between them.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/03/06/diamtree.jpg)
>
> ```
> Input: root = [1,2,3,4,5]
> Output: 3
> Explanation: 3 is the length of the path [4,2,1,3] or [5,2,1,3].
> ```

{% hint style="info" %}
找到左右最大深度 连起来就是 直径
{% endhint %}

```
class Solution {
    int sum = 0;
    public int diameterOfBinaryTree(TreeNode root) {
        maxDepth(root);
        return sum;
    }
    private int maxDepth(TreeNode root){
        if(root == null) return 0;
        int left = maxDepth(root.left);
        int right = maxDepth(root.right);
        sum = Math.max(left + right, sum);
        return Math.max(left, right) + 1;
    }
}
```
