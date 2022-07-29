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



碰到二叉树的问题，就想想整棵树在该问题上的结果 和左右儿子在该问题上的结果之间的联系是什么

![](<.gitbook/assets/image (11) (2).png>)



1. Divide & Conquer可以**自定义参数向下传额外的信息**，并通过return value向上传递返回值，典型例子_Sum Root to Leaf Numbers_&#x20;
2. Stack可用来模拟recursion，curt != null来判断入栈条件，!stack.isEmpty()用来判断出栈条件。二者均为在recursion中的出口。
3. Divide & Conquer是bottom-up的方式，traversal是top-down的方式。
