# Find the Duplicate Number

[https://leetcode.com/problems/find-the-duplicate-number/](https://leetcode.com/problems/find-the-duplicate-number/)

共有n+ 1个数字 取值range 是\[1, n] 必有一个重复数字 找到重复的数字

> Given an array of integers `nums` containing `n + 1` integers where each integer is in the range `[1, n]` inclusive.
>
> There is only **one repeated number** in `nums`, return _this repeated number_.
>
> You must solve the problem **without** modifying the array `nums` and uses only constant extra space.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [1,3,4,2,2]
> Output: 2
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [3,1,3,4,2]
> Output: 3
> ```

{% hint style="info" %}
对答案进行二分   在1 - n中找到是大于号的当前数即可  因为在1-n中取值 n+1个数 如果当前数不是重复的 小于等于当前数的个数 肯定是小于等于当前数的
{% endhint %}

```
class Solution {
    public int findDuplicate(int[] nums) {
        int left = 0, right = nums.length - 1;
        while(left + 1 < right){
            int mid = (right - left) / 2 + left;
            if(cnt(nums, mid) <= mid){
                left = mid;
            }else{
                right = mid;
            }
        }
        if(cnt(nums, left) <= left) return right;
        return left;
    }
    private int cnt(int[] nums, int mid){
        int cnt = 0;
        for(int num : nums){
            if(num <= mid){
                cnt++;
            }
        }
        return cnt;
    }
}
```
