# Recover Binary Search Tree

[https://leetcode.com/problems/recover-binary-search-tree/](https://leetcode.com/problems/recover-binary-search-tree/)

> You are given the `root` of a binary search tree (BST), where the values of **exactly** two nodes of the tree were swapped by mistake. _Recover the tree without changing its structure_.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2020/10/28/recover1.jpg)
>
> ```
> Input: root = [1,3,null,null,2]
> Output: [3,1,null,null,2]
> Explanation: 3 cannot be a left child of 1 because 3 > 1. Swapping 1 and 3 makes the BST valid.
> ```
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2020/10/28/recover2.jpg)
>
> ```
> Input: root = [3,1,4,null,null,2]
> Output: [2,1,4,null,null,3]
> Explanation: 2 cannot be in the right subtree of 3 because 2 < 3. Swapping 2 and 3 makes the BST valid.
> ```

```
class Solution {
    TreeNode pre = null;
    TreeNode first = null;
    TreeNode second = null;
    public void recoverTree(TreeNode root) {
        if(root == null) return;
        inorder(root);
        if(first != null && second != null) {
            int tmp = first.val;
            first.val = second.val;
            second.val = tmp;
        }
    }
    private void inorder(TreeNode root){
        if(root == null) return;
        inorder(root.left);
        if(pre != null && root.val <= pre.val){
            if(first == null){
                first = pre;
                second = root;
            }else{
                second = root;
            }
        }
        pre = root;
        inorder(root.right);
    }
}
```
