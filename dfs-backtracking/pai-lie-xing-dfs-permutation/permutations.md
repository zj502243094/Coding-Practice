# Permutations

[https://leetcode.com/problems/permutations/](https://leetcode.com/problems/permutations/)

> Given an array `nums` of **distinct** integers, return _all the possible permutations_. You can return the answer in **any order**.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: nums = [1,2,3]
> <strong>Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]</strong></code></pre>
>
> **Example 2:**
>
> <pre><code>Input: nums = [0,1]
> <strong>Output:[[0,1],[1,0]]</strong></code></pre>
>
> **Example 3:**
>
> <pre><code>Input: nums = [1]
> <strong>Output: [[1]]</strong></code></pre>

```
class Solution {
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        boolean[] visit = new boolean[nums.length];
        dfs(nums, visit, new ArrayList<>(), res);
        return res;
    }
    private void dfs(int[] nums, boolean[] visit, List<Integer> cur, List<List<Integer>> res) {
        if (cur.size() == nums.length) {
            res.add(new ArrayList<>(cur));
            return;
        }
        for (int i = 0; i < nums.length; i++) {
            if (visit[i]) continue;
            cur.add(nums[i]);
            visit[i] = true;
            dfs(nums, visit, cur, res);
            cur.remove(cur.size() - 1);
            visit[i] = false;
        }
    }
}
```

```
class Solution {
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        dfs(nums, new ArrayList<>(), res);
        return res;
    }
    private void dfs(int[] nums, List<Integer> cur, List<List<Integer>> res) {
        if (cur.size() == nums.length) {
            res.add(new ArrayList<>(cur));
            return;
        }
        for (int i = 0; i < nums.length; i++) {
            if (cur.contains(nums[i])) continue;
            cur.add(nums[i]);
            dfs(nums, cur, res);
            cur.remove(cur.size() - 1);
        }
    }
}
```
