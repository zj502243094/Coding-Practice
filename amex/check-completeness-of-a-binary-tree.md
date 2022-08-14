# Check Completeness of a Binary Tree

[https://leetcode.com/problems/check-completeness-of-a-binary-tree/](https://leetcode.com/problems/check-completeness-of-a-binary-tree/)

> Given the `root` of a binary tree, determine if it is a _complete binary tree_.
>
>
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2018/12/15/complete-binary-tree-1.png)
>
> <pre><code>Input: root = [1,2,3,4,5,6]
> <strong>Output:true
> </strong><strong>Explanation:
> </strong> Every level before the last is full (ie. levels with node-values {1} and {2, 3}), and all nodes in the last level ({4, 5, 6}) are as far left as possible.</code></pre>
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2018/12/15/complete-binary-tree-2.png)
>
> <pre><code>Input: root = [1,2,3,4,5,null,7]
> <strong>Output:false
> </strong><strong>Explanation:The node with value 7 isn't as far left as possible.</strong></code></pre>

{% hint style="info" %}
从左到右弹 直到 遇到空 如果Queue中还有数字 表白 右边还有 false
{% endhint %}

```
class Solution {
    public boolean isCompleteTree(TreeNode root) {
        Queue<TreeNode> q = new LinkedList();
        q.offer(root);
        while (!q.isEmpty()) {
            TreeNode cur = q.poll();
            if (cur == null && q.peek() != null) return false;
            if (cur != null) {
                q.offer(cur.left);
                q.offer(cur.right);
            }
        }
        return true;
    }
}
```

```
class Solution {
    public boolean isCompleteTree(TreeNode root) {
        if (root == null) return true;
        Queue<TreeNode> q = new LinkedList<>();
        boolean empty = false;
        q.offer(root);
        while (!q.isEmpty()) {
            TreeNode cur = q.poll();
            if (cur == null) {
                empty = true;
            } else {
                if (empty) return false;
                q.offer(cur.left);
                q.offer(cur.right);
            } 
        }
        return true;
    }
}
```
