# Binary Tree

Binary Tree实现

```
/**
 * Definition of TreeNode:
 * public class TreeNode {
 *     public int val;
 *     public TreeNode left, right;
 *     public TreeNode(int val) {
 *         this.val = val;
 *         this.left = this.right = null;
 *     }
 * }
 */
```

A **full** binary tree is a tree in which every node has either 0 or 2 children.

In a **complete** binary tree every level, except possibly the last, is completely filled, and all nodes in the last level are as far left as possible.

A **balanced** binary tree is a binary tree structure in which the left and right subtrees of every node differ in height by no more than 1.

A **perfect** binary tree is a tree with all leaves are at the same level, and every parent has two children.

先序遍历（Preorder traversal）根左右

<img src=".gitbook/assets/image (9).png" alt="" data-size="original">

中序遍历（Inorder traversal）左根右

![](<.gitbook/assets/image (8).png>)

后序遍历（Postorder traversal） 左右根 1 4 7 6 3 13 14 10 8

```
private class Main{
    public static void main(String[] args) {
        TreeNode node1 = new TreeNode(8);
        TreeNode node2 = new TreeNode(3);
        TreeNode node3 = new TreeNode(10);
        
        node1.left = node2;
        node1.right = node3;
        
        Solution solution = new Solution();
        solution.xxx(node1)
    }
}

class Solution{
    public void xxx(TreeNode x){
    }
}
```
