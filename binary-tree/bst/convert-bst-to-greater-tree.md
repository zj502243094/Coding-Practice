# Convert BST to Greater Tree

[https://leetcode.com/problems/convert-bst-to-greater-tree/](https://leetcode.com/problems/convert-bst-to-greater-tree/)

返回一个当前节点和大于此节点和的 root

> Given the `root` of a Binary Search Tree (BST), convert it to a Greater Tree such that every key of the original BST is changed to the original key plus the sum of all keys greater than the original key in BST.
>
> As a reminder, a _binary search tree_ is a tree that satisfies these constraints:
>
> * The left subtree of a node contains only nodes with keys **less than** the node's key.
> * The right subtree of a node contains only nodes with keys **greater than** the node's key.
> * Both the left and right subtrees must also be binary search trees.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2019/05/02/tree.png)
>
> ```
> Input: root = [4,1,6,0,2,5,7,null,null,null,3,null,null,null,8]
> Output: [30,36,21,36,35,26,15,null,null,null,33,null,null,null,8]
> ```

{% hint style="info" %}
先遍历右边 再root 再左边 sum += root.val
{% endhint %}

```
class Solution {
    int sum = 0;
    public TreeNode convertBST(TreeNode root) {
        covert(root);
        return root;
    }
    private void covert(TreeNode root){
        if(root == null) return;
        covert(root.right);
        sum += root.val;
        root.val = sum;
        covert(root.left);
    }
}
```
