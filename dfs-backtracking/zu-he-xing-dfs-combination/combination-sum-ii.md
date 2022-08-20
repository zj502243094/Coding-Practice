# Combination Sum II

[https://leetcode.com/problems/combination-sum-ii/submissions/](https://leetcode.com/problems/combination-sum-ii/submissions/)

nums\[] 和为target 不可以重复使用&#x20;

```
class Solution {
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        List<List<Integer>> res = new ArrayList<>();
        Arrays.sort(candidates);
        dfs(candidates, 0, target, new ArrayList<>(), res);
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
            dfs(nums, i + 1, target - nums[i], cur, res);
            cur.remove(cur.size() - 1);
        }
    }
}
```
