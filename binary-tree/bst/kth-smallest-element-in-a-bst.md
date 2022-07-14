# Kth Smallest Element in a BST

[https://leetcode.com/problems/kth-smallest-element-in-a-bst/](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)

> Given the `root` of a binary search tree, and an integer `k`, return _the_ `kth` _smallest value (**1-indexed**) of all the values of the nodes in the tree_.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/01/28/kthtree1.jpg)
>
> ```
> Input: root = [3,1,4,null,2], k = 1
> Output: 1
> ```
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2021/01/28/kthtree2.jpg)
>
> ```
> Input: root = [5,3,6,2,4,null,null,1], k = 3
> Output: 3
> ```

```
class Solution {
    public int kthSmallest(TreeNode root, int k) {
        List<Integer> res = new ArrayList<>();
        inorder(root, res);
        return res.get(k - 1);
    }
    private List<Integer> inorder(TreeNode root, List<Integer> res){
        if(root == null) return res;
        inorder(root.left, res);
        res.add(root.val);
        inorder(root.right, res);
        return res;
    }
}
```
