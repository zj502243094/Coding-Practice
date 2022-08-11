# Binary Tree Vertical Order Traversal

[https://leetcode.com/problems/binary-tree-vertical-order-traversal/](https://leetcode.com/problems/binary-tree-vertical-order-traversal/)

> Given the `root` of a binary tree, return _**the vertical order traversal** of its nodes' values_. (i.e., from top to bottom, column by column).
>
> If two nodes are in the same row and column, the order should be from **left to right**.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/01/28/vtree1.jpg)
>
> <pre><code>Input: root = [3,9,20,null,null,15,7]
> <strong>Output: [[9],[3,15],[20],[7]]</strong></code></pre>
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2021/01/28/vtree2-1.jpg)
>
> <pre><code>Input: root = [3,9,8,4,0,1,7]
> <strong>Output: [[4],[9],[3,0,1],[8],[7]]</strong></code></pre>

```
class Solution {
    public List<List<Integer>> verticalOrder(TreeNode root) {
        List<List<Integer>> res = new ArrayList<>();
        Map<TreeNode, Integer> position = new HashMap();
        Map<Integer, List<Integer>> colToRoot = new HashMap();
        position.put(root, 0);
        
        Queue<TreeNode> q = new LinkedList();
        if (root != null) q.offer(root);
        int pos = 0;
        while (!q.isEmpty()) {
            TreeNode cur = q.poll();
            int col = position.get(cur);
            colToRoot.computeIfAbsent(col, x -> new ArrayList()).add(cur.val);
            if (cur.left != null) {
                q.offer(cur.left);
                position.put(cur.left, col - 1);
            }
            if (cur.right != null) {
                q.offer(cur.right);
                position.put(cur.right, col + 1);
            }
            pos = Math.min(pos, col);
        }
        while (colToRoot.containsKey(pos)) {
            res.add(colToRoot.get(pos++));
        }
        return res;
    }
}
```
