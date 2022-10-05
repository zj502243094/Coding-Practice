# Binary Tree Zigzag Level Order Traversal

[https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)

```
class Solution {
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        List<List<Integer>> res = new ArrayList();
        if (root == null) return res;
        Queue<TreeNode> q = new LinkedList();
        q.offer(root);
        while (!q.isEmpty()) {
            int size = q.size();
            List<Integer> level = new ArrayList();
            for (int i = 0; i < size; i++) {
                TreeNode cur = q.poll();
                if (res.size() % 2 == 0) level.add(cur.val);
                else level.add(0, cur.val);
                if (cur.left != null) q.offer(cur.left);
                if (cur.right != null) q.offer(cur.right);
            }
            res.add(level);
        }
        return res;
    }
}
```

```
class Solution {
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        List<List<Integer>> res = new ArrayList<>();
        dfs(root, 0, res);
        return res;
    }
    private void dfs(TreeNode root, int height, List<List<Integer>> res) {
        if (root == null) return;
        if (height >= res.size()) res.add(new ArrayList<>());
        if (height % 2 == 0)  res.get(height).add(root.val);
        else res.get(height).add(0, root.val);
        if (root.left != null) dfs(root.left, height + 1, res);
        if (root.right != null) dfs(root.right, height + 1, res);
    }
}
```
