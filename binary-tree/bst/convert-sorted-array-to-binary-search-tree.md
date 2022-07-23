# Convert Sorted Array to Binary Search Tree

[https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)

排序过的数组 转成 BST&#x20;

> Given an integer array `nums` where the elements are sorted in **ascending order**, convert _it to a **height-balanced** binary search tree_.
>
> A **height-balanced** binary tree is a binary tree in which the depth of the two subtrees of every node never differs by more than one.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/02/18/btree1.jpg)
>
> ```
> Input: nums = [-10,-3,0,5,9]
> Output: [0,-3,9,-10,null,5]
> Explanation: [0,-10,5,null,-3,null,9] is also accepted:
> ```
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2021/02/18/btree.jpg)
>
> ```
> Input: nums = [1,3]
> Output: [3,1]
> Explanation: [1,null,3] and [3,1] are both height-balanced BSTs.
> ```

```
class Solution {
    public TreeNode sortedArrayToBST(int[] nums) {
        if(nums == null) return null;
        return helper(nums, 0, nums.length - 1);
    }
    private TreeNode helper(int[] nums, int left, int right){
        if(left > right) return null;
        int mid = (right - left) / 2 + left;
        TreeNode root = new TreeNode(nums[mid]);
        root.left = helper(nums, left, mid - 1);
        root.right = helper(nums, mid + 1, right);
        return root;
    }
}
```
