# Max Consecutive Ones III

[https://leetcode.com/problems/max-consecutive-ones-iii/](https://leetcode.com/problems/max-consecutive-ones-iii/)

> Given a binary array `nums` and an integer `k`, return _the maximum number of consecutive_ `1`_'s in the array if you can flip at most_ `k` `0`'s.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [1,1,1,0,0,0,1,1,1,1,0], k = 2
> Output: 6
> Explanation: [1,1,1,0,0,1,1,1,1,1,1]
> ```

```
class Solution {
    public int longestOnes(int[] nums, int k) {
        int res = 0;
        if (nums == null || nums.length == 0) return res;
        
        int l = 0, r = 0;
        int zero = 0;
        while (r < nums.length) {
            if (nums[r] == 0) {
                zero++;
            }
            r++;
            if (zero > k) {
                if (nums[l] == 0) {
                    zero--;
                }
                l++;
            }
            res = Math.max(res, r - l);
        }
        return res;
    }
}
```
