# Binary Tree Right Side View

[https://leetcode.com/problems/binary-tree-right-side-view/](https://leetcode.com/problems/binary-tree-right-side-view/)\
只返回tree 最右侧node

> Given the `root` of a binary tree, imagine yourself standing on the **right side** of it, return _the values of the nodes you can see ordered from top to bottom_.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/02/14/tree.jpg)
>
> ```
> Input: root = [1,2,3,null,5,null,4]
> Output: [1,3,4]
> ```

{% hint style="info" %}
本行最后一个 加入&#x20;

如果是left view i == 0 的时候加入
{% endhint %}

```
class Solution {
    public List<Integer> rightSideView(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        Queue<TreeNode> q = new LinkedList<>();
        if (root != null) q.offer(root);
        while (!q.isEmpty()) {
            int size = q.size();
            int val = 0;
            for (int i = 0; i < size; i++) {
                TreeNode cur = q.poll();
                if (i == size - 1) res.add(cur.val);
                if (cur.left != null) q.offer(cur.left);
                if (cur.right != null) q.offer(cur.right);
            }
        }
        return res;
    } 
}
```

{% hint style="info" %}
按找到当前行 先找右边 就是right view

先找左边就是 leftview
{% endhint %}

```
class Solution {
    public List<Integer> rightSideView(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        if(root == null) return res;
        rightView(root, res, 0);
        return res;
    }
    private void rightView(TreeNode root, List<Integer> res, int curHeight){
        if(root == null) return;
        if(curHeight == res.size()) res.add(root.val);
        rightView(root.right, res, curHeight + 1);
        rightView(root.left, res, curHeight + 1);
    }
}
```
