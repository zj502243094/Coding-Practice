# Inorder Successor in BST

在一个BST里面 找到一个节点的后继 后继 是正好比他大的节点

[https://leetcode.com/problems/inorder-successor-in-bst/](https://leetcode.com/problems/inorder-successor-in-bst/)

> Given the `root` of a binary search tree and a node `p` in it, return _the in-order successor of that node in the BST_. If the given node has no in-order successor in the tree, return `null`.
>
> The successor of a node `p` is the node with the smallest key greater than `p.val`.
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2019/01/23/285\_example\_1.PNG)
>
> ```
> Input: root = [2,1,3], p = 1
> Output: 2
> Explanation: 1's in-order successor node is 2. Note that both p and the return value is of TreeNode type.
> ```
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2019/01/23/285\_example\_2.PNG)
>
> ```
> Input: root = [5,3,6,2,4,null,null,1], p = 6
> Output: null
> Explanation: There is no in-order successor of the current node, so the answer is null.
> ```

{% hint style="info" %}
root <= p 右子树&#x20;

root > p root 或左子树
{% endhint %}



```
class Solution {
    public TreeNode inorderSuccessor(TreeNode root, TreeNode p) {
        if(root == null || p == null) return null; 
        
        if(root.val <= p.val){
            return inorderSuccessor(root.right, p);
        }else{
            TreeNode leftMax = inorderSuccessor(root.left, p);
            if(leftMax == null) return root;
            else return leftMax;
        }
    }
}
```

```
class Solution {
    public TreeNode inorderSuccessor(TreeNode root, TreeNode p) {
        TreeNode res = null;
        
        while(root != null){
            if(root.val > p.val){
                res = root;
                root = root.left;
            }else{
                root = root.right;
            }
        }
        return res;
    }
}
```
