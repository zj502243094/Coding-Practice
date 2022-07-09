# Construct Binary Tree from Inorder and Postorder Traversal

[https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/)

> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/02/19/tree.jpg)
>
> ```
> Input: inorder = [9,3,15,20,7], postorder = [9,15,7,20,3]
> Output: [3,9,20,null,null,15,7]
> ```

```
class Solution {
    public TreeNode buildTree(int[] inorder, int[] postorder) {
        int len = postorder.length;
        if(len == 0) return null;
        int val = postorder[len - 1];
        TreeNode root = new TreeNode(val);
        
        int index = -1;
        for(int i = 0; i < len; i++){
            if(inorder[i] == val) index = i;
        }
        
        int[] left_in = Arrays.copyOfRange(inorder, 0, index);
        int[] right_in = Arrays.copyOfRange(inorder, index + 1, len);
        int[] left_post = Arrays.copyOfRange(postorder, 0, index);
        int[] right_post = Arrays.copyOfRange(postorder, index, len - 1);
        
        root.left = buildTree(left_in, left_post);
        root.right = buildTree(right_in, right_post);
        return root;
    }
}
```
