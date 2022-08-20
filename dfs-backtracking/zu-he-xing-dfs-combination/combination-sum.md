# Combination Sum

[https://leetcode.com/problems/combination-sum/](https://leetcode.com/problems/combination-sum/)

nums\[] 和为target 可以重复使用&#x20;

> Given an array of **distinct** integers `candidates` and a target integer `target`, return _a list of all **unique combinations** of_ `candidates` _where the chosen numbers sum to_ `target`_._ You may return the combinations in **any order**.
>
> The **same** number may be chosen from `candidates` an **unlimited number of times**. Two combinations are unique if the frequency of at least one of the chosen numbers is different.
>
> It is **guaranteed** that the number of unique combinations that sum up to `target` is less than `150` combinations for the given input.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: candidates = [2,3,6,7], target = 7
> <strong>Output: [[2,2,3],[7]]</strong></code></pre>
>
>
>
> **Example 2:**
>
> <pre><code>Input: candidates = [2,3,5], target = 8
> <strong>Output: [[2,2,2,2],[2,3,3],[3,5]]</strong></code></pre>

{% hint style="info" %}
<pre><code><strong>dfs(nums, i, target - nums[i], cur, res);</strong></code></pre>

因为可以使用重复元素 所以用 i 而不用 i + 1;
{% endhint %}

```
class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> res = new ArrayList<>();
        Arrays.sort(candidates);
        dfs(candidates, 0, target, new ArrayList<Integer>(), res);
        return res;
    } 
    private void dfs(int[] nums, int index, int target, List<Integer> cur, List<List<Integer>> res) {
        if (target == 0) {
            res.add(new ArrayList<>(cur));
        }
        for (int i = index; i < nums.length; i++) {
            if (i > index && nums[i] == nums[i - 1]) {
                continue;
            } else if (nums[i] > target) {
                break;
            }
            
            cur.add(nums[i]);
            dfs(nums, i, target - nums[i], cur, res);
            cur.remove(cur.size() - 1);
        }
    } 
}
```

```
class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> res = new ArrayList<>();
        Arrays.sort(candidates);
        List<Integer> nums = new ArrayList<>();
        for (int i = 0; i < candidates.length; i++) {
            if (i > 0 && candidates[i] == candidates[i - 1]) continue;
            nums.add(candidates[i]);
        }
        dfs(nums, 0, target, new ArrayList<Integer>(), res);
        return res;
    } 
    private void dfs(List<Integer> nums, int index, int target, List<Integer> cur, List<List<Integer>> res) {
        if (index == nums.size()) {
            if (target == 0) {
                res.add(new ArrayList<>(cur));
            }
            return;
        }
        for (int cnt = 0; cnt * nums.get(index) <= target; cnt++) {
            for (int i = 0; i < cnt; i++) {
                cur.add(nums.get(index));
            }
            dfs (nums, index + 1, target - cnt * nums.get(index), cur, res);
            for (int i = 0; i < cnt; i++) {
                cur.remove(cur.size() - 1);
            }
        }
    } 
}
```
