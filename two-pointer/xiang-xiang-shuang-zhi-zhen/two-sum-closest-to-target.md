# Two Sum - Closest to target

[https://www.lintcode.com/problem/533/](https://www.lintcode.com/problem/533/)

> Given an array `nums` of _n_ integers, find two integers in _nums_ such that the sum is closest to a given number, _target_.
>
> Return the absolute value of difference between the sum of the two numbers and the target.
>
> ***
>
> Example
>
> **Example1**
>
> ```
> Input:  nums = [-1, 2, 1, -4] and target = 4
> Output: 1
> Explanation:
> The minimum difference is 1. (4 - (2 + 1) = 1).
> ```
>
> **Example2**
>
> ```
> Input:  nums = [-1, -1, -1, -4] and target = 4
> Output: 6
> Explanation:
> The minimum difference is 6. (4 - (- 1 - 1) = 6).
> ```

{% hint style="info" %}
排序后 如果nums\[l] + nums\[r] < target 左端点动 否则右端点动
{% endhint %}

```
public class Solution {
    /**
     * @param nums: an integer array
     * @param target: An integer
     * @return: the difference between the sum and the target
     */
    public int twoSumClosest(int[] nums, int target) {
        int res = Integer.MAX_VALUE;
        if(nums == null || nums.length == 0) return res;
        Arrays.sort(nums);

        int l = 0, r = nums.length - 1;
        while(l < r){
            int sum = nums[l] + nums[r];
            res = Math.min(res, Math.abs(target - sum));
            if(sum < target){
                l++;
            }else if(sum > target){
                r--;
            }else{
                break;
            }
        }
        return res;
    }
}
```

```
public class Solution {
    /**
     * @param nums: an integer array
     * @param target: An integer
     * @return: the difference between the sum and the target
     */
    public int twoSumClosest(int[] nums, int target) {
        int res = Integer.MAX_VALUE;
        if(nums == null || nums.length == 0) return res;
        Arrays.sort(nums);

        int l = 0, r = nums.length - 1;
        while(l < r){
            int sum = nums[l] + nums[r];
            res = Math.min(res, Math.abs(target - sum));
            if(sum < target){
                l++;
            }else{
                r--;
            }
        }
        return res;
    }
}
```
