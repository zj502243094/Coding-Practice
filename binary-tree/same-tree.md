# Same Tree

> Given the roots of two binary trees `p` and `q`, write a function to check if they are the same or not.
>
> Two binary trees are considered the same if they are structurally identical, and the nodes have the same value.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2020/12/20/ex1.jpg)
>
> ```
> Input: p = [1,2,3], q = [1,2,3]
> Output: true
> ```
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2020/12/20/ex2.jpg)
>
> ```
> Input: p = [1,2], q = [1,null,2]
> Output: false
> ```

{% hint style="info" %}
if(p == null && q == null) return true; \
if(p == null || q == null) return false;
{% endhint %}

```
class Solution {
    public boolean isSameTree(TreeNode p, TreeNode q) {
        if(p == null || q == null) return p == q;
        if(p.val != q.val) return false;
        return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
    }
}
```
