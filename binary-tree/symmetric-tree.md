# Symmetric Tree

[https://leetcode.com/problems/symmetric-tree/description/](https://leetcode.com/problems/symmetric-tree/description/)

> Given the `root` of a binary tree, _check whether it is a mirror of itself_ (i.e., symmetric around its center).
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/02/19/symtree1.jpg)
>
> <pre><code><strong>Input: root = [1,2,2,3,4,4,3]
> </strong><strong>Output: true
> </strong></code></pre>
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2021/02/19/symtree2.jpg)
>
> <pre><code><strong>Input: root = [1,2,2,null,3,null,3]
> </strong><strong>Output: false
> </strong></code></pre>

{% hint style="info" %}
The left and right subtrees are mirror images:

* `left.val == right.val`
* `left.left` mirrors `right.right`
* `left.right` mirrors `right.left`
{% endhint %}

```
class Solution {
    public boolean isSymmetric(TreeNode root) {
        if (root == null) return true;
        return isMirror(root.left, root.right);
    }
    private boolean isMirror(TreeNode t1, TreeNode t2) {
        if (t1 == null && t2 == null) return true;
        if (t1 == null || t2 == null) return false;
        return (t1.val == t2.val) 
            && isMirror(t1.left, t2.right)
            && isMirror(t2.left, t1.right);
    }
}
```
