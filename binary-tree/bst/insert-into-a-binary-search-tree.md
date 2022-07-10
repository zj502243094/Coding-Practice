# Insert into a Binary Search Tree

[https://leetcode.com/problems/insert-into-a-binary-search-tree/](https://leetcode.com/problems/insert-into-a-binary-search-tree/)

> You are given the `root` node of a binary search tree (BST) and a `value` to insert into the tree. Return _the root node of the BST after the insertion_. It is **guaranteed** that the new value does not exist in the original BST.
>
> **Notice** that there may exist multiple valid ways for the insertion, as long as the tree remains a BST after insertion. You can return **any of them**.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2020/10/05/insertbst.jpg)
>
> ```
> Input: root = [4,2,7,1,3], val = 5
> Output: [4,2,7,1,3,5]
> ```

```
class Solution {
    public TreeNode insertIntoBST(TreeNode root, int val) {
        TreeNode node = new TreeNode(val);
        if(root == null) return node;
        
        if(root.val > val) {
            root.left = insertIntoBST(root.left, val);
        } else {
            root.right = insertIntoBST(root.right, val);
        }
        return root;
    }
}
```

```
class Solution {
    public TreeNode insertIntoBST(TreeNode root, int val) {
        TreeNode node = new TreeNode(val);
        if(root == null) return node;
        
        TreeNode dummy = null;
        TreeNode cur = root;
        while(cur != null){
            dummy = cur;
            if(cur.val < val){
                cur = cur.right;
            } else {
                cur = cur.left;
            }
        }
        if(dummy.val > val) dummy.left = node;
        else dummy.right = node;
        return root;
    }
}
```
