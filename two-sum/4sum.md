# 4Sum

[https://leetcode.com/problems/4sum/](https://leetcode.com/problems/4sum/)

> Given an array `nums` of `n` integers, return _an array of all the **unique** quadruplets_ `[nums[a], nums[b], nums[c], nums[d]]` such that:
>
> * `0 <= a, b, c, d < n`
> * `a`, `b`, `c`, and `d` are **distinct**.
> * `nums[a] + nums[b] + nums[c] + nums[d] == target`
>
> You may return the answer in **any order**.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: nums = [1,0,-1,0,-2,2], target = 0
> <strong>Output:
> </strong> [[-2,-1,1,2],[-2,0,0,2],[-1,0,0,1]]</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: nums = [2,2,2,2,2], target = 8
> <strong>Output:
> </strong> [[2,2,2,2]]</code></pre>

```
class Solution {
    public List<List<Integer>> fourSum(int[] nums, int target) {
        Arrays.sort(nums);
        List<List<Integer>> res = new ArrayList<>();
        long sum = 0;
        int n = nums.length;
        for (int i = 0; i < n - 3; i++) {
            if (i > 0 && nums[i] == nums[i - 1]) continue;
            long tar3 = target - nums[i];
            for (int j = i + 1; j < n - 2; j++) {
                if (j > i + 1 && nums[j] == nums[j - 1]) continue;
                long tar2 = tar3 - nums[j];
                int l = j + 1;
                int r = n - 1;
                while (l < r) {
                    sum = nums[l] + nums[r];
                    if (sum == tar2) {
                        res.add(List.of(nums[i], nums[j], nums[l++], nums[r--]));
                        while (l < r && nums[l] == nums[l - 1]) l++;
                        while (l < r && nums[r] == nums[r + 1]) r--;
                    } else if (sum > tar2) {
                        r--;
                    } else {
                        l++;
                    }
                }
            }
        }
        return res;
    }
}
```
