# Search Range in Binary Search Tree

> Description
>
> Given a binary search tree and a range `[k1, k2]`, return node values within a given range in ascending order.
>
> Example
>
> **Example 1:**
>
> Input:
>
> ```
> tree = {5}
> k1 = 6
> k2 = 10
> ```
>
> Output:
>
> ```
> []
> ```
>
> Explanation:
>
> No number between 6 and 10
>
> **Example 2:**
>
> Input:
>
> ```
> tree = {20,8,22,4,12}
> k1 = 10
> k2 = 22
> ```
>
> Output:
>
> ```
> [12,20,22]
> ```

{% hint style="info" %}
root.val > k1 向左找  root.val < k2 向右找 找到 K1 K2的范围 之间的加上
{% endhint %}

```
public class Solution {
    List<Integer> res = new ArrayList<>();
    public List<Integer> searchRange(TreeNode root, int k1, int k2) {
        if(root == null) return res;
        search(root, k1, k2);
        return res;
    }
    private void search(TreeNode root, int k1, int k2){
        if(root == null) return;
        if(root.val > k1) search(root.left, k1, k2);
        if(root.val >= k1 && root.val <= k2) res.add(root.val);
        if(root.val < k2) search(root.right, k1, k2);
    }
}
```
