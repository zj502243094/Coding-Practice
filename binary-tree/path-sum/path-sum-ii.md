# Path Sum II

[https://leetcode.com/problems/path-sum-ii/](https://leetcode.com/problems/path-sum-ii/)

> Given the `root` of a binary tree and an integer `targetSum`, return _all **root-to-leaf** paths where the sum of the node values in the path equals_ `targetSum`_. Each path should be returned as a list of the node **values**, not node references_.
>
> A **root-to-leaf** path is a path starting from the root and ending at any leaf node. A **leaf** is a node with no children.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/01/18/pathsumii1.jpg)
>
> ```
> Input: root = [5,4,8,11,null,13,4,7,2,null,null,5,1], targetSum = 22
> Output: [[5,4,11,2],[5,8,4,5]]
> Explanation: There are two paths whose sum equals targetSum:
> 5 + 4 + 11 + 2 = 22
> 5 + 8 + 4 + 5 = 22
> ```

```
class Solution {
    public List<List<Integer>> pathSum(TreeNode root, int targetSum) {
        List<List<Integer>> res = new ArrayList<>();
        if(root == null) return res;
        
        List<Integer> path = new ArrayList<>();
        helper(root, targetSum, path, res);
        return res;
    }
    private void helper(TreeNode root, int targetSum, List<Integer> path, List<List<Integer>> res){
        if(root == null) return;
        path.add(root.val);
        if(root.left == null && root.right == null && root.val == targetSum) {
            res.add(new ArrayList<>(path));
        } 
        helper(root.left, targetSum - root.val, path, res);
        helper(root.right, targetSum - root.val, path, res);
        path.remove(path.size() - 1);
    }
}
```
