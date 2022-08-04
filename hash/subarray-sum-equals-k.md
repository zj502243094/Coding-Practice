# Subarray Sum Equals K

[https://leetcode.com/problems/subarray-sum-equals-k/](https://leetcode.com/problems/subarray-sum-equals-k/)

子数组和为K

> Given an array of integers `nums` and an integer `k`, return _the total number of subarrays whose sum equals to_ `k`.
>
> A subarray is a contiguous **non-empty** sequence of elements within an array.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [1,1,1], k = 2
> Output: 2
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [1,2,3], k = 3
> Output: 2
> ```

{% hint style="info" %}
前缀和数组    用前缀和 与 出现的的次数 做一个map
{% endhint %}

```
class Solution {
    public int subarraySum(int[] nums, int k) {
        int res = 0;
        if (nums == null || nums.length == 0) return res;
        int sum = 0;
        Map<Integer, Integer> map = new HashMap();
        map.put(0, 1);
        
        for (int i = 0; i < nums.length; i++) {
            sum += nums[i];
            if (map.containsKey(sum - k)) res += map.get(sum - k);
            map.put(sum, map.getOrDefault(sum, 0) + 1);
        }
        return res;
    }
}
```
