# Flatten Binary Tree to Linked List

[https://leetcode.com/problems/flatten-binary-tree-to-linked-list/](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/)

> Given the `root` of a binary tree, flatten the tree into a "linked list":
>
> * The "linked list" should use the same `TreeNode` class where the `right` child pointer points to the next node in the list and the `left` child pointer is always `null`.
> * The "linked list" should be in the same order as a [**pre-order traversal**](https://en.wikipedia.org/wiki/Tree\_traversal#Pre-order,\_NLR) of the binary tree.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/01/14/flaten.jpg)
>
> ```
> Input: root = [1,2,5,3,4,null,6]
> Output: [1,null,2,null,3,null,4,null,5,null,6]
> ```

{% hint style="info" %}
按照POST order 遍历BT 左右根

右边存起来 node.right into right and then set node.right to node.left\
然后右边不为空的时候讲 node.right 和右边连上
{% endhint %}

```
class Solution {
    public void flatten(TreeNode root) {
        if(root == null) return;
        flatten(root.left);
        flatten(root.right);
        TreeNode left = root.left;
        TreeNode right = root.right;
        root.left = null;
        root.right = left;
        while(root.right != null) {
            root = root.right;
        }
        root.right = right;
    }
}
```

{% hint style="info" %}
因为 结果需要 按照根左右  所以按照右左根的顺序遍历 root.right 直线前一点 再连上
{% endhint %}

```
class Solution {
    private TreeNode pre = null;
    public void flatten(TreeNode root) {
        if(root == null) return;
        flatten(root.right);
        flatten(root.left);
        root.right = pre;
        root.left = null;
        pre = root;
    }
}
```

#### ![](<../.gitbook/assets/image (8) (1).png>)
