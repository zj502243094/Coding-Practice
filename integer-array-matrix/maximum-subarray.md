# Maximum Subarray

[https://leetcode.com/problems/maximum-subarray/](https://leetcode.com/problems/maximum-subarray/)

找到返回有最大和的subarray

> Given an integer array `nums`, find the contiguous subarray (containing at least one number) which has the largest sum and return _its sum_.
>
> A **subarray** is a **contiguous** part of an array.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
> Output: 6
> Explanation: [4,-1,2,1] has the largest sum = 6.
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [1]
> Output: 1
> ```
>
> **Example 3:**
>
> ```
> Input: nums = [5,4,-1,7,8]
> Output: 23
> ```

{% hint style="info" %}
先求前缀和 最大的前缀减最小的前缀 就是最大的subarray 前缀和 前一个数的前缀加当前数
{% endhint %}

```
class Solution {
    public int maxSubArray(int[] nums) {
        if(nums == null || nums.length == 0) return Integer.MIN_VALUE;
        int res = Integer.MIN_VALUE;
        
        int[] sum = new int[nums.length + 1];
        for(int i = 1; i <= nums.length; i++){
            sum[i] = sum[i - 1] + nums[i - 1];
        }
        int minS = Integer.MAX_VALUE;
        for(int i = 1; i <= nums.length; i++){
            minS = Math.min(minS, sum[i - 1]);
            int s = sum[i] - minS;
            res = Math.max(s, res);
        }
        return res;
    }
}
```
