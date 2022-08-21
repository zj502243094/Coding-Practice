# Combination Sum III

[https://leetcode.com/problems/combination-sum-iii/](https://leetcode.com/problems/combination-sum-iii/)

```
class Solution {
    public List<List<Integer>> combinationSum3(int k, int n) {
        int[] nums = new int[9];
        for (int i = 1; i <= 9; i++) nums[i - 1] = i;
        List<List<Integer>> res = new ArrayList<>();
        dfs (nums, 0, k, n, new ArrayList<>(), res);
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
