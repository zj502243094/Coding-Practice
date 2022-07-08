# Binary Tree Leaf Sum

[https://www.lintcode.com/problem/481/](https://www.lintcode.com/problem/481/)

> Given a binary tree, calculate the sum of leaves.
>
> **样例**
>
> **Example 1:**
>
> ```
> Input：{1,2,3,4}
> Output：7
> Explanation：
>     1
>    / \
>   2   3
>  /
> 4
> 3+4=7
> ```
>
> **Example 2:**
>
> ```
> Input：{1,#,3}
> Output：3
> Explanation：
>     1
>       \
>        3
> ```

```
public class Solution {
    /**
     * @param root: the root of the binary tree
     * @return: An integer
     */
    public int leafSum(TreeNode root) {
        if(root == null) return 0;
        if(root.left == null && root.right == null) return root.val;
        int left = leafSum(root.left);
        int right = leafSum(root.right);

        return left + right;
    }
}
```
