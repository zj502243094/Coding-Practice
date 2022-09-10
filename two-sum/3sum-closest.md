# 3Sum Closest

[https://leetcode.com/problems/3sum-closest/](https://leetcode.com/problems/3sum-closest/)

> Given an integer array `nums` of length `n` and an integer `target`, find three integers in `nums` such that the sum is closest to `target`.
>
> Return _the sum of the three integers_.
>
> You may assume that each input would have exactly one solution.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: nums = [-1,2,1,-4], target = 1
> <strong>Output:
> </strong> 2
> <strong>Explanation:
> </strong> The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: nums = [0,0,0], target = 1
> <strong>Output:
> </strong> 0</code></pre>

```
class Solution {
    public int threeSumClosest(int[] nums, int target) {
        int n = nums.length;
        int res = nums[0] + nums[1] + nums[n - 1];
        Arrays.sort(nums);
        for (int i = 0; i < n - 2; i++) {
            int l = i + 1, r = n - 1;
            while (l < r) {
                int sum = nums[i] + nums[l] + nums[r];
                if (Math.abs(sum - target) < Math.abs(res - target)) res = sum;
                if (sum > target) r--;
                else l++;
            }
        }
        return res;
    }
}
```
