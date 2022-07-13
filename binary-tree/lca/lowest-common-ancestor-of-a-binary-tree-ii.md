# Lowest Common Ancestor of a Binary Tree II

[https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree-ii/](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree-ii/)

{% hint style="info" %}
上面 follow up 因为p、q不一定在tree里面 所以需要遍历完整个树后 再确定返回root
{% endhint %}

> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2018/12/14/binarytree.png)
>
> ```
> Input: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1
> Output: 3
> Explanation: The LCA of nodes 5 and 1 is 3.
> ```
>
> **Example 2:**
>
> <img src="https://assets.leetcode.com/uploads/2018/12/14/binarytree.png" alt="" data-size="original">
>
> ```
> Input: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4
> Output: 5
> Explanation: The LCA of nodes 5 and 4 is 5. A node can be a descendant of itself according to the definition of LCA.
> ```

```
class Solution {
    boolean foundP = false;
    boolean foundQ = false;
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        TreeNode res = LCA(root, p, q);
        if(foundP && foundQ) return res;
        return null;
    }
    private TreeNode LCA(TreeNode root, TreeNode p, TreeNode q){
        if(root == null) return null;
        TreeNode left = LCA(root.left, p, q);
        TreeNode right = LCA(root.right, p, q);
        
        
        if(root == p || root == q) {
            if(root == p) foundP = true;
            if(root == q) foundQ = true;
            return root;
        }
        
        if(left != null && right != null) return root;
        if(left != null) return left;
        if(right != null) return right;
        return null;
    }
}
```
