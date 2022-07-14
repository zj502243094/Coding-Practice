# Find Leaves of Binary Tree

[https://leetcode.com/problems/find-leaves-of-binary-tree/](https://leetcode.com/problems/find-leaves-of-binary-tree/)

> Given the `root` of a binary tree, collect a tree's nodes as if you were doing this:
>
> * Collect all the leaf nodes.
> * Remove all the leaf nodes.
> * Repeat until the tree is empty.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/03/16/remleaves-tree.jpg)
>
> ```
> Input: root = [1,2,3,4,5]
> Output: [[4,5,3],[2],[1]]
> Explanation:
> [[3,5,4],[2],[1]] and [[3,4,5],[2],[1]] are also considered correct answers since per each level it does not matter the order on which elements are returned.
> ```
>
> **Example 2:**
>
> ```
> Input: root = [1]
> Output: [[1]]
> ```

```
class Solution {
    public List<List<Integer>> findLeaves(TreeNode root) {
        List<List<Integer>> res = new ArrayList<>();
        if(root == null) return res;
        findLeaf(root, res);
        return res;
    }
    private int findLeaf(TreeNode root, List<List<Integer>> res){
        if(root == null) return -1;
        int left = findLeaf(root.left, res);
        int right = findLeaf(root.right, res);
        int height = Math.max(left, right) + 1;
        if (res.size() < height + 1){
            res.add(new ArrayList<>());
        }
        res.get(height).add(root.val);
        return height;
    }
}
```
