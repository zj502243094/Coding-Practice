# Subsets II

[https://leetcode.com/problems/subsets-ii/](https://leetcode.com/problems/subsets-ii/)

返回nums 全部的子集合 并且不重复

> Given an integer array `nums` that may contain duplicates, return _all possible subsets (the power set)_.
>
> The solution set **must not** contain duplicate subsets. Return the solution in **any order**.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: nums = [1,2,2]
> <strong>Output:[[],[1],[1,2],[1,2,2],[2],[2,2]]</strong></code></pre>
>
> **Example 2:**
>
> <pre><code>Input: nums = [0]
> <strong>Output:[[],[0]]</strong></code></pre>

```
class Solution {
    public List<List<Integer>> subsetsWithDup(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        Arrays.sort(nums);
        dfs(nums, 0, new ArrayList<>(), res);
        return res;
    }
    private void dfs(int[] nums, int index, List<Integer> cur, List<List<Integer>> res) {
        res.add(new ArrayList<>(cur));
        for (int i = index; i < nums.length; i++) {
            if (i > index && nums[i] == nums[i - 1]) continue;
            cur.add(nums[i]);
            dfs(nums, i + 1, cur, res);
            cur.remove(cur.size() - 1);
        }
    }
}
```
