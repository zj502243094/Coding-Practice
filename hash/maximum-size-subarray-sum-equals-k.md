# Maximum Size Subarray Sum Equals k

[https://leetcode.com/problems/maximum-size-subarray-sum-equals-k/](https://leetcode.com/problems/maximum-size-subarray-sum-equals-k/)

> Given an integer array `nums` and an integer `k`, return _the maximum length of a subarray that sums to_ `k`. If there is not one, return `0` instead.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [1,-1,5,-2,3], k = 3
> Output: 4
> Explanation: The subarray [1, -1, 5, -2] sums to 3 and is the longest.
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [-2,-1,2,1], k = 1
> Output: 2
> Explanation: The subarray [-1, 2] sums to 1 and is the longest.
> ```

```
class Solution {
    public int maxSubArrayLen(int[] nums, int k) {
        int res = 0;
        if (nums == null || nums.length == 0) return res;
        int sum = 0;
        Map<Integer, Integer> map = new HashMap();
        
        for (int i = 0; i < nums.length; i++) {
            sum += nums[i];
            if (sum == k) res = i + 1;
            if (map.containsKey(sum - k)) res = Math.max(res, i - map.get(sum - k));
            map.putIfAbsent(sum, i);
        }
        return res;
    }
}
```
