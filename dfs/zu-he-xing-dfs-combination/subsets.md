# Subsets

[https://leetcode.com/problems/subsets/](https://leetcode.com/problems/subsets/)

返回nums 全部的子集合

> Given an integer array `nums` of **unique** elements, return _all possible subsets (the power set)_.
>
> The solution set **must not** contain duplicate subsets. Return the solution in **any order**.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: nums = [1,2,3]
> <strong>Output:[[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]</strong></code></pre>
>
> **Example 2:**
>
> <pre><code>Input: nums = [0]
> <strong>Output: [[],[0]]</strong></code></pre>

![](<../../.gitbook/assets/image (5).png>)

```
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        dfs(nums, 0, new ArrayList<>(), res);
        return res;
    }
    private void dfs(int[] nums, int index, List<Integer> cur, List<List<Integer>> res) {
        res.add(new ArrayList<>(cur));
        for (int i = index; i < nums.length; i++) {
            cur.add(nums[i]);
            dfs(nums, i + 1, cur, res);
            cur.remove(cur.size() - 1);
        }
    }
}
```

![](<../../.gitbook/assets/image (2).png>)

```
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        if (nums == null || nums.length == 0) return res;
        dfs(nums, 0, new ArrayList<>(), res);
        return res;
    }
    private void dfs(int[] nums, int index, List<Integer> cur, List<List<Integer>> res) {
        if (index == nums.length) {
            res.add(new ArrayList<>(cur));
            return;
        }
        cur.add(nums[index]);
        dfs(nums, index + 1, cur, res);
        cur.remove(cur.size() - 1);
        dfs(nums, index + 1, cur, res);
    }
}
```
