# Check Full Binary Tree

> A full binary tree is defined as a binary tree in which all nodes have either zero or two child nodes. Conversely, there is no node in a full binary tree, which has one child node. More information about full binary trees can be found [here](https://baike.baidu.com/item/%E6%BB%A1%E4%BA%8C%E5%8F%89%E6%A0%91).
>
> ```
> Full Binary Tree
>       1
>      / \
>     2   3
>    / \
>   4   5
>
> Not a Full Binary Tree
>       1
>      / \
>     2   3
>    / 
>   4   
> ```

```
class Solution {
    public boolean isFullBinaryTree(TreeNode root) {
        if (root == null) return true;
        if (root.left == null && root.right == null) return true;
        if (root.left != null && root.right != null) {
            return isFullBinaryTree(root.left) && isFullBinaryTree(root.right);
        }
        return false;
    }
}
```

```
class Solution {
    public boolean isFullBinaryTree(TreeNode root) {
        Queue<TreeNode> q = new LinkedList<>();
        if (root != null) q.offer(root);
        while (!q.isEmpty()) {
            TreeNode cur = q.poll();
            if (cur.left == null &&  cur.right == null) {
                continue;
            } else {
               return false; 
            }
            q.offer(cur.left);
            q.offer(cur.right);
        }
        return true;
    }
}
```
