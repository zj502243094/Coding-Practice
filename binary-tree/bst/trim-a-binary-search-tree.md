# Trim a Binary Search Tree

[https://leetcode.com/problems/trim-a-binary-search-tree/](https://leetcode.com/problems/trim-a-binary-search-tree/)

> Given the `root` of a binary search tree and the lowest and highest boundaries as `low` and `high`, trim the tree so that all its elements lies in `[low, high]`. Trimming the tree should **not** change the relative structure of the elements that will remain in the tree (i.e., any node's descendant should remain a descendant). It can be proven that there is a **unique answer**.
>
> Return _the root of the trimmed binary search tree_. Note that the root may change depending on the given bounds.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2020/09/09/trim1.jpg)
>
> ```
> Input: root = [1,0,2], low = 1, high = 2
> Output: [1,null,2]
> ```
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2020/09/09/trim2.jpg)
>
> ```
> Input: root = [3,0,4,null,2,null,null,1], low = 1, high = 3
> Output: [3,2,null,1]
> ```

{% hint style="info" %}
1. 如果 root.val < min 直接对root.right进行修剪&#x20;
2. 如果 root.val > max 直接对root.left进行修剪
3. root.val 在之间 对左右进行trim

![](<../../.gitbook/assets/image (10).png>)
{% endhint %}

```
class Solution {
    public TreeNode trimBST(TreeNode root, int low, int high) {
        if(root == null) return null;
        if(root.val < low){
            return trimBST(root.right, low, high);
        }else if(root.val > high){
            return trimBST(root.left, low, high);
        }else{
            root.left = trimBST(root.left, low, high);
            root.right = trimBST(root.right, low, high);
        }
        return root;
    }
}
```
