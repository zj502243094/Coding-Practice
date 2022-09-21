# Boundary of Binary Tree

[https://leetcode.com/problems/boundary-of-binary-tree/](https://leetcode.com/problems/boundary-of-binary-tree/)

> The **boundary** of a binary tree is the concatenation of the **root**, the **left boundary**, the **leaves** ordered from left-to-right, and the **reverse order** of the **right boundary**.
>
> The **left boundary** is the set of nodes defined by the following:
>
> * The root node's left child is in the left boundary. If the root does not have a left child, then the left boundary is **empty**.
> * If a node in the left boundary and has a left child, then the left child is in the left boundary.
> * If a node is in the left boundary, has **no** left child, but has a right child, then the right child is in the left boundary.
> * The leftmost leaf is **not** in the left boundary.
>
> The **right boundary** is similar to the **left boundary**, except it is the right side of the root's right subtree. Again, the leaf is **not** part of the **right boundary**, and the **right boundary** is empty if the root does not have a right child.
>
> The **leaves** are nodes that do not have any children. For this problem, the root is **not** a leaf.
>
> Given the `root` of a binary tree, return _the values of its **boundary**_.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2020/11/11/boundary1.jpg)
>
> <pre><code>Input: root = [1,null,2,3,4]
> <strong>Output:
> </strong> [1,3,4,2]
> Explanation:
> - The left boundary is empty because the root does not have a left child.
> - The right boundary follows the path starting from the root's right child 2 -> 4.
>   4 is a leaf, so the right boundary is [2].
> - The leaves from left to right are [3,4].
> Concatenating everything results in [1] + [] + [3,4] + [2] = [1,3,4,2].</code></pre>
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2020/11/11/boundary2.jpg)
>
> <pre><code>Input: root = [1,2,3,4,5,6,null,null,null,7,8,9,10]
> <strong>Output:
> </strong> [1,2,4,7,8,9,10,6,3]</code></pre>

```
class Solution {
    public List<Integer> boundaryOfBinaryTree(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        if (root == null) return res;
        res.add(root.val);
        if(root.left != null || root.right != null) {
            addLeft(root.left, res);
            addLeaves(root, res);
            addRight(root.right, res);
        }
        return res;
    }
    
    private void addLeft(TreeNode root, List<Integer> res) {
        if (root == null) return;
        if (root.left != null || root.right != null) res.add(root.val);
        if (root.left != null) {
            addLeft(root.left, res);
        } else if (root.right != null) {
            addLeft(root.right, res);
        } 
    }
    
    private void addLeaves(TreeNode root, List<Integer> res) {
        if (root == null) return;
        if (root.left == null && root.right == null) res.add(root.val);
        addLeaves(root.left, res);
        addLeaves(root.right, res);
    }
    
    private void addRight(TreeNode root, List<Integer> res) {
        if (root == null) return;
        if (root.right != null) {
            addRight(root.right, res);
        } else if (root.left != null) {
            addRight(root.left, res);
        }
        if (root.left != null || root.right != null) res.add(root.val);
    }
}
```
