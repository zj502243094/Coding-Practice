# Construct Binary Tree from Preorder and Inorder Traversal

[https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)

> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/02/19/tree.jpg)
>
> ```
> Input: preorder = [3,9,20,15,7], inorder = [9,3,15,20,7]
> Output: [3,9,20,null,null,15,7]
> ```

{% hint style="info" %}
Arrays.copyOfRange(original, from, to)
{% endhint %}

```
class Solution {
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        int len = preorder.length;
        if(len == 0) return null;
        int val = preorder[0];
        TreeNode root = new TreeNode(val);
        
        int index = -1;
        for(int i = 0; i < inorder.length; i++){
            if(inorder[i] == val) index = i;
        }
        
        int[] left_pre = Arrays.copyOfRange(preorder, 1, index + 1);
        int[] right_pre = Arrays.copyOfRange(preorder, index + 1, len);
        int[] left_in = Arrays.copyOfRange(inorder, 0, index);
        int[] right_in = Arrays.copyOfRange(inorder, index + 1, len);
        
        root.left = buildTree(left_pre, left_in);
        root.right = buildTree(right_pre, right_in);
        return root;
    }
}
```
