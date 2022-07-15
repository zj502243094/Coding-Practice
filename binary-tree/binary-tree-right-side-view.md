# Binary Tree Right Side View

[https://leetcode.com/problems/binary-tree-right-side-view/](https://leetcode.com/problems/binary-tree-right-side-view/)

> Given the `root` of a binary tree, imagine yourself standing on the **right side** of it, return _the values of the nodes you can see ordered from top to bottom_.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/02/14/tree.jpg)
>
> ```
> Input: root = [1,2,3,null,5,null,4]
> Output: [1,3,4]
> ```

```
class Solution {
    public List<Integer> rightSideView(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        if(root == null) return res;
        rightView(root, res, 0);
        return res;
    }
    private void rightView(TreeNode root, List<Integer> res, int curHeight){
        if(root == null) return;
        if(curHeight == res.size()) res.add(root.val);
        rightView(root.right, res, curHeight + 1);
        rightView(root.left, res, curHeight + 1);
    }
}
```
