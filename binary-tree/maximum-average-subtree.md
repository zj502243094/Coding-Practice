# Maximum Average Subtree

[https://leetcode.com/problems/maximum-average-subtree/](https://leetcode.com/problems/maximum-average-subtree/)

> Description
>
> Given a binary tree, find the subtree with maximum average. Return the root of the subtree.
>
> ***
>
> *
>
> LintCode will print the subtree which root is your return node.\
> It's guaranteed that there is only one subtree with maximum average.
>
> Example
>
> **Example 1**
>
> ```
> Input：
> {1,-5,11,1,2,4,-2}
> Output：11
> Explanation:
> The tree is look like this:
>      1
>    /   \
>  -5     11
>  / \   /  \
> 1   2 4    -2 
> The average of subtree of 11 is 4.3333, is the maximun.
> ```
>
> **Example 2**
>
> ```
> Input：
> {1,-5,11}
> Output：11
> Explanation:
>      1
>    /   \
>  -5     11
> The average of subtree of 1,-5,11 is 2.333,-5,11. So the subtree of 11 is the maximun
> ```

```
class Solution {
    double maxAvg = Double.MIN_VALUE;
    
    public double maximumAverageSubtree(TreeNode root) {
        getSum(root);
        return maxAvg;
    }
    
    private int getSum(TreeNode root){
        if(root == null) return 0;
        int sum = getSum(root.left) + getSum(root.right) + root.val;
        int nodes = countNode(root.left) + countNode(root.right) + 1;
        double avg = (double)sum / (double)nodes;
        if(avg > maxAvg){
            maxAvg = avg;
        }
        return sum;
    }
    
    private int countNode(TreeNode root){
        if(root == null) return 0;
        return countNode(root.left) + countNode(root.right) + 1;
    }
}
```
