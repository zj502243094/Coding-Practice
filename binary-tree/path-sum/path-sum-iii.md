# Path Sum III

[https://leetcode.com/problems/path-sum-iii/](https://leetcode.com/problems/path-sum-iii/)

从任意节点开始 有几个节点的和为 target

> Given the `root` of a binary tree and an integer `targetSum`, return _the number of paths where the sum of the values along the path equals_ `targetSum`.
>
> The path does not need to start or end at the root or a leaf, but it must go downwards (i.e., traveling only from parent nodes to child nodes).
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/04/09/pathsum3-1-tree.jpg)
>
> ```
> Input: root = [10,5,-3,3,2,null,11,3,-2,null,1], targetSum = 8
> Output: 3
> Explanation: The paths that sum to 8 are shown.
> ```

{% hint style="info" %}
check() find the number of solutions that starting at the root, it doesn't matter where it ends.
{% endhint %}

```
class Solution {
    public int pathSum(TreeNode root, int targetSum) {
        if(root == null) return 0;
        int count = check(root, targetSum);
        return count + pathSum(root.left, targetSum) + pathSum(root.right, targetSum);
    }
    private int check(TreeNode root, int target){
        if(root == null) return 0;
        int cnt = 0;
        if(root.val == target){
            cnt++;
        }
        return cnt + check(root.left, target - root.val) + check(root.right, target - root.val);
    }
}
```

路径：

![](<../../.gitbook/assets/image (4) (1) (2).png>)
