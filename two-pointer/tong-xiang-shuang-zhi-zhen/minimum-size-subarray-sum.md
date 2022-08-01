# Minimum Size Subarray Sum

[https://leetcode.com/problems/minimum-size-subarray-sum/](https://leetcode.com/problems/minimum-size-subarray-sum/)\
[https://www.lintcode.com/problem/406/](https://www.lintcode.com/problem/406/)

给正数数组 返回最短的连续数组 和 大于或等于 target 的数组长度

> Given an array of positive integers `nums` and a positive integer `target`, return the minimal length of a **contiguous subarray** `[numsl, numsl+1, ..., numsr-1, numsr]` of which the sum is greater than or equal to `target`. If there is no such subarray, return `0` instead.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: target = 7, nums = [2,3,1,2,4,3]
> Output: 2
> Explanation: The subarray [4,3] has the minimal length under the problem constraint.
> ```
>
> **Example 2:**
>
> ```
> Input: target = 4, nums = [1,4,4]
> Output: 1
> ```
>
> **Example 3:**
>
> ```
> Input: target = 11, nums = [1,1,1,1,1,1,1,1]
> Output: 0
> ```

{% hint style="info" %}
如果满足`sum >=` target，就可以修改sl，让`sum -= nums[i]`，同时记录比较最小的区间长度，直到内层循环让`sum >=` target的条件不再满足。外层循环的条件则是`j`遍历到达数组的末尾。
{% endhint %}

{% hint style="success" %}
Time complexity: O(n)   Space complexity: O(1)
{% endhint %}

```
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        int l = 0, r = 0;
        int res = Integer.MAX_VALUE;
        int sum = 0;
        while(r < nums.length){
            sum += nums[r];
            while(sum >= target){
                res = Math.min(res, r - l + 1);
                sum -= nums[l];
                l++;
            }
            r++;
        }
        return res == Integer.MAX_VALUE ? 0 : res;
    }
}
```

```
public int minimumSize(int[] nums, int s) {
        if(s < 0 || nums == null || nums.length == 0) return -1;
        int res = Integer.MAX_VALUE;
        int sum = 0;
        int r = 0;
        for(int l = 0; l < nums.length; l++){
            while(r < nums.length && sum < s){
                sum += nums[r];
                r++;
            }
            if(sum >= s) res = Math.min(r - l, res);
            sum -= nums[l];
        }
        return res == Integer.MAX_VALUE ? -1 : res;
    }
```

{% hint style="info" %}
虽然数组nums\[]本身没有排序过，但是因为元素均为正数，前缀和prefix sum其实是一个严格递增的数组，因此确定了starting index之后，可以用binary search寻找ending index。\
二分法 找的target 应该是 sum\[i] + target
{% endhint %}

{% hint style="success" %}
Time: O(nlogn) - outer loop O(n), binary search in each loop O(logn), thus O(n \* logn)

Space O(n) - additional prefix sum array O(n)
{% endhint %}

```
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        if (nums == null || nums.length == 0) {
            return 0;
        }
        int[] sums = new int[nums.length + 1];
        for (int i = 1; i < sums.length; i++){
            sums[i] = sums[i - 1] + nums[i - 1];
        }
        int res = Integer.MAX_VALUE;
        for(int i = 0; i < nums.length; i++){
            int end = binarySearch(sums, i, sums[i] + target);
            if(end == -1) break;
            res = Math.min(res, end - i);
        }
        return res == Integer.MAX_VALUE ? 0 : res;
    }
    private int binarySearch(int[] sums, int left, int target){
        int right = sums.length - 1;
        while(left + 1 < right){
            int mid = (right - left) / 2 + left;
            if(sums[mid] >= target){
                right = mid;
            }else{
                left = mid;
            }
        }
        if(sums[right] >= target) return right;
        if(sums[left] >= target) return left;
        return -1;
    }
}
```
