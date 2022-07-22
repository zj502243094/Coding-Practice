# Closest Binary Search Tree Value

[https://leetcode.com/problems/closest-binary-search-tree-value/](https://leetcode.com/problems/closest-binary-search-tree-value/)

> Given the `root` of a binary search tree and a `target` value, return _the value in the BST that is closest to the_ `target`.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/03/12/closest1-1-tree.jpg)
>
> ```
> Input: root = [4,2,5,1,3], target = 3.714286
> Output: 4
> ```
>
> **Example 2:**
>
> ```
> Input: root = [1], target = 4.428571
> Output: 1
> ```

```
class Solution {
    int res = 0;
    double min = Double.MAX_VALUE;
    public int closestValue(TreeNode root, double target) {
        dfs(root, target);
        return res;
    }
    private void dfs(TreeNode root, double target){
        if(root == null) return;
        if(Math.abs(root.val - target) < min){
            min = Math.abs(root.val - target);
            res = root.val;
        }
        if(root.val < target) dfs(root.right, target);
        else dfs(root.left, target);
    }
}
```
