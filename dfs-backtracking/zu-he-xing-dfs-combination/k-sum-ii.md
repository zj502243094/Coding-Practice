# k Sum II

[https://www.lintcode.com/problem/90/](https://www.lintcode.com/problem/90/)

在a\[]里面选k个数和为target

> Given `n` distinct positive integers, the integer `k`  and a target number.
>
> Find `k` distinct numbers within these `n` numbers such that the sum of these `k` numbers equals the target number, and you need to find all the solutions that satisfy the requirement (the order of the solutions is not required).
>
> Example
>
> **Example 1:**
>
> Input:
>
> ```
> array = [1,2,3,4]
> k = 2
> target = 5
> ```
>
> Output:
>
> ```
> [[1,4],[2,3]]
> ```
>
> **Example 2:**
>
> Input:
>
> ```
> array = [1,3,4,6]
> k = 3
> target = 8
> ```
>
> Output:
>
> ```
> [[1,3,4]]
> ```

```
public class Solution {

    public List<List<Integer>> kSumII(int[] a, int k, int target) {
        List<List<Integer>> res = new ArrayList<>();
        dfs(a, 0, k, target, new ArrayList<>(), res);
        return res;
    }
    private void dfs(int[] nums, int index, int k, int target, List<Integer> cur, List<List<Integer>> res) {
        if (k == 0) {
            if (target == 0) {
                res.add(new ArrayList<>(cur));
            }
            return;
        }
        if (target < 0 || index == nums.length) {
            return;
        } 
        cur.add(nums[index]);
        dfs(nums, index + 1, k - 1, target - nums[index], cur, res);
        cur.remove(cur.size() - 1);
        dfs(nums, index + 1, k, target, cur, res);
    }
}
```

```
public List<List<Integer>> kSumII(int[] a, int k, int target) {
        List<List<Integer>> res = new ArrayList<>();
        dfs(a, 0, k, target, new ArrayList<>(), res);
        return res;
    }
    private void dfs(int[] nums, int index, int k, int target, List<Integer> cur, List<List<Integer>> res) {
        if (k == 0) {
            if (target == 0) {
                res.add(new ArrayList<>(cur));
            }
            return;
        }
        if (target < 0) {
            return;
        } 
        for (int i = index; i < nums.length; i++) {
            cur.add(nums[i]);
            dfs(nums, i + 1, k - 1, target - nums[i], cur, res);
            cur.remove(cur.size() - 1);
        }
    }
```
