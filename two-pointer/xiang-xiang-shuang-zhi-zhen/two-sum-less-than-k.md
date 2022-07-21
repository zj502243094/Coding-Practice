# Two Sum Less Than K

[https://leetcode.com/problems/two-sum-less-than-k/](https://leetcode.com/problems/two-sum-less-than-k/)

> Given an array `nums` of integers and integer `k`, return the maximum `sum` such that there exists `i < j` with `nums[i] + nums[j] = sum` and `sum < k`. If no `i`, `j` exist satisfying this equation, return `-1`.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [34,23,1,24,75,33,54,8], k = 60
> Output: 58
> Explanation: We can use 34 and 24 to sum 58 which is less than 60.
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [10,20,30], k = 15
> Output: -1
> Explanation: In this case it is not possible to get a pair sum less that 15.
> ```

```
class Solution {
    public int twoSumLessThanK(int[] nums, int k) {
        int res = - 1;
        if(nums == null || nums.length == 0) return res;
        Arrays.sort(nums);
        
        int l = 0, r = nums.length - 1;
        while(l < r){
            int sum = nums[l] + nums[r];
            if(sum >= k){
                r--;
            }else{
                if(sum > res){
                    res = sum;
                }
                l++;
            }
        }
        return res;
    }
}
```
