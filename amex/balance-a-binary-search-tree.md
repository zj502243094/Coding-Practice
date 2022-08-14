# Balance a Binary Search Tree

[https://leetcode.com/problems/balance-a-binary-search-tree/](https://leetcode.com/problems/balance-a-binary-search-tree/)

平衡一个BST 左右相差不超过1

> Given the `root` of a binary search tree, return _a **balanced** binary search tree with the same node values_. If there is more than one answer, return **any of them**.
>
> A binary search tree is **balanced** if the depth of the two subtrees of every node never differs by more than `1`.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/08/10/balance1-tree.jpg)
>
> ```
> Input: root = [1,null,2,null,3,null,4,null,null]
> Output: [2,1,3,null,null,null,4]
> Explanation: This is not the only correct answer, [3,1,4,null,2] is also correct.
> ```
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2021/08/10/balanced2-tree.jpg)
>
> ```
> Input: root = [2,1,3]
> Output: [2,1,3]
> ```

{% hint style="info" %}
上一题 套的 先将 BST 压平成 sorted array 然后再建成BST；
{% endhint %}

```
class Solution {
    public TreeNode balanceBST(TreeNode root) {
        if(root == null) return null;
        List<Integer> nums = new ArrayList<>();
        helper(root, nums);
        return build(nums, 0, nums.size() - 1);
    }
    
    private void helper(TreeNode root, List<Integer> nums){
        if(root == null) return;
        helper(root.left, nums);
        nums.add(root.val);
        helper(root.right, nums);
    }
    
    private TreeNode build(List<Integer> nums, int left, int right){
        if(left > right) return null;
        int mid = (right - left) / 2 + left;
        TreeNode root = new TreeNode(nums.get(mid));
        root.left = build(nums, left, mid - 1);
        root.right = build(nums, mid + 1, right);
        return root;
    }
}
```
