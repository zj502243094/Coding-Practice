# Max Consecutive Ones

[https://leetcode.com/problems/max-consecutive-ones/](https://leetcode.com/problems/max-consecutive-ones/)

连续为 1 最长的数

> Given a binary array `nums`, return _the maximum number of consecutive_ `1`_'s in the array_.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [1,1,0,1,1,1]
> Output: 3
> Explanation: The first two digits or the last three digits are consecutive 1s. The maximum number of consecutive 1s is 3.
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [1,0,1,1,0,1]
> Output: 2
> ```

{% hint style="info" %}
每次遇到 为 1 的数 count ++ 遇到为0的数 count 归零
{% endhint %}

```
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int res = 0;
        if (nums == null || nums.length == 0) return res;
        
        int count = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == 1) {
                count++;
                res = Math.max(count, res);
            } else {
                count = 0;
            }
        }
        return res;
    }
}
```

{% hint style="info" %}
同向双指针 找到第一个为 1 的值

然后 r = l; 直到 r 为最后一个1&#x20;

最后l = r 找下一个连续1
{% endhint %}

```
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int res = 0;
        if (nums == null || nums.length == 0) return res;
        
        int l = 0, r = 0;
        while (l < nums.length) {
            while (l < nums.length && nums[l] != 1) {
                l++;
            }
            r = l;
            while (r < nums.length && nums[r] == 1) {
                r++;
            }
            res = Math.max(r - l, res);
            l = r;
        }
        return res;
    }
}
```
