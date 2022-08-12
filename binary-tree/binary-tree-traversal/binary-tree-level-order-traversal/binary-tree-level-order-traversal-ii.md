# Binary Tree Level Order Traversal II

[https://leetcode.com/problems/binary-tree-level-order-traversal-ii/](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/)

```
class Solution {
    public List<List<Integer>> levelOrderBottom(TreeNode root) {
        List<List<Integer>> res = new ArrayList();
        if (root == null) return res;
        Queue<TreeNode> q = new LinkedList();
        q.offer(root);
        while (!q.isEmpty()) {
            int size = q.size();
            List<Integer> level = new ArrayList();
            for (int i = 0; i < size; i++) {
                TreeNode cur = q.poll();
                level.add(cur.val);
                if (cur.left != null) q.offer(cur.left);
                if (cur.right != null) q.offer(cur.right);
            }
            res.add(0, level);  // res.add(level);
        }
        return res;   // Collections.reverse(res);
    }
}
```
